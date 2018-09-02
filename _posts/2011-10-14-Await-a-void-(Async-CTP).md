---
layout: post
title: Await a void (Async CTP)
tags: 
category: General
---
I am really enjoying getting more and more into the new async ctp. Something that stumped me up to now, was how do I run a void method asynchronously.

For instance, suppose I have the following workflow that I want to run.

        private void DoWorkFlowSync()
        {
            txtStatus.Text = "Step 1";
            Step1Workflow();
            txtStatus.Text = "Step 2";
            Step2Workflow();
            txtStatus.Text = "Step 3";
            Step3Workflow();
            txtStatus.Text = "Done";
        }
        
        private void Step1Workflow()
        {            
            Thread.Sleep(1000);             
        }

        private void Step2Workflow()
        {
            Thread.Sleep(1000);            
        }

        private void Step3Workflow()
        {
            Thread.Sleep(1000);            
        }
 

This is it in its synchronous state, if I try and run it asynchronously my initial attempts would be to code the DoWorkFlowSync as follows.

 

        private async void DoWorkFlowAsync()
        {
            txtStatus.Text = "Step 1";
            await Step1Workflow();
            txtStatus.Text = "Step 2";
            await Step2Workflow();
            txtStatus.Text = "Step 3";
            await Step3Workflow();
            txtStatus.Text = "Done";
        }
To which the compiler would respond with a compile time error with the following…

Error    1    Cannot await 'void’

So, a bit of a dilemma. I don’t want to have to rewrite each individual method (i.e. Step1Wroflow) to be of type Task. It would be doable if this was a small project but I want to be able to refactor large projects with appropriate asynchronous calls without going to deep into the project. Eventually I made a mind shift and found the following to work.

        private async void DoWorkFlowAsync()
        {
            txtStatus.Text = "Step 1";
            await TaskEx.Run(() => Step1Workflow());
            txtStatus.Text = "Step 2";
            await TaskEx.Run(() => Step2Workflow());
            txtStatus.Text = "Step 3";
            await TaskEx.Run(() => Step3Workflow());
            txtStatus.Text = "Done";
        }
This worked perfectly, the UI was responsive and I have a workflow that is easy to read.

For those that are interested in learning more about the new async ctp go to the forum