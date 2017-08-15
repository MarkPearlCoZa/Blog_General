---
layout: post
title: Pair Programming Illuminated by Williams and Kessler
tags: 
category: Media
---

## Chapter 1

* Don't force people to pair, it involves breaking old habits and being more communicative & collaborative than we've been conditioned to be
* When we talk about pairing, we include design and testing in the "programming" part  

## Chapter 2 - 7 Myths of Pair Programming

* Resistance to pair programming comes due to misconceptions from top down (from management) and from bottom up (from engineers)  
* The misconceptions are often reasonable and rational, but incorrect assumptions  
* Pair programming is very intense, have "pair programming hours"
* Some pair programmers say that they feel uncomfortable working alone after getting used to pairing  
* Pair programming works well with most partners, the one partner that people battle with is the "My way or the highway" partner  
* In pairing an expert with a novice, the expert needs to be willing to take on the role  
* Need to transition from getting satisfaction on doing things on our own to satisfaction on the team succeeding  
* Give 'drivers' an opportunity to fix their own spelling or typo mistakes instead of the navigator pointing it out straight away  
* Speaks about the difference between mental flow and block and how pairs are easier to keep mental flow and make breakthroughs with mental blocks  

1. It will double the workload with two doing the work one can do.  
2. I'll never get to work alone.  
3. It will work well only with the right partner.  
4. Pair programming is good for training, but once you know what you are doing it is a waste of time.  
5. I'll never get credit for doing anything. I'll have to share recognition.
6. The navigator finds only syntax mistakes, surely the compiler can do that.  
7. The only time I ever get any real work done is when I'm alone.  

Tom Demarco on flow or "the zone" in Peopleware...

~~~
Flow is a condition of deep, nearly meditative involvement. In this state, there is a gentle sense of euphoria, and one is largely unaware of the passage of time... There is no consciousness of effort; the work just seems to, well, flow... Not all work roles require that you attain a state of flow in order to be productive, but for anyone involved in engineering design, development, writing, or similar tasks, flow is a must. These are high-momentum tasks. It's only when you're in a flow that work goes well.
~~~

## Chapter 3 - The Seven Synergistic Behaviors of Pair Programming

1. Pair Pressure, put positive pressure on each person to do their best  
2. Pair Negotiation, arrive at the best solution together  
3. Pair Courage, having a partner gives you courage to do things you wouldn't do on your own  
4. Pair Reviews, you pick up defects earlier and don't miss the obvious  
5. Pair Debugging, problems are resolved through the act of explaining them to another  
6. Pair Learning, knowledge is constantly being passed between partners, from tool usage to programming language rules, to design  
7. Pair Trust,  pairs begin to trust each other  

## Chapter 4 - Overcoming Management Resistance to Pair Programming  

Managers need to know that pairing will help them achieve their objectives  

What's in it for managers:
* I want to complete my projects on time with high-quality code  
* I want to reduce my risk of losing a key person  
* I want my employees to be happy  
* I want to reduce the amount of time it takes to train a new person  
* I want my teams to work well together and to communicate more effectively and efficiently with each other  

## Chapter 5 - Gaining support and acceptance from your peers

Start small, get buy in with small groups and then re-evaluate once you have seen value
Not too much else in this chapter

## Chapter 6 - Transitioning to Pair Programming by Choice

* Mentions a Pair Programming readiness survey

Developers are more satisfied with using software development innovations if:  
* they have increased choice in when to use that innovation  
* they have decreased process control in how to use that innovation
* their manager encouraged them to use the innovative technique (getting balance between "not forcing" and "not caring" is tough)  

Technique for adopting, get senior respected technical person to try it and get them convinced this is the way to go. If they are convinced then get them to prepare a tutorial around it. Find early adopters to experiment. Evaluate and collect data. Propose organizational guidelines for use of technique (e.g. times to do it etc).  

## Chapter 7 - Problem, Problems  

* Dependency, you get used to it and it is hard working alone  
* Scheduling, getting everyone's schedules to match can be a challenge  
* The Ever Popular Expert, people want to pair with experts when they are doing certain things. Can reduce the benefit of learning / flattening out knowledge  
* Co-location, people need to be together although there are tools to do remote pairing  
* Noise & Facilities, pairs are noiser than solo's and require larger work areas than cubicles  
* Concentration, some people struggle to concentrate and be creative when working with a partner
* Disagreements, people disagree and it get's heated  
* Rushing, sometimes having a pair can encourage you to rush to completion
* Skill imbalances, can be frustrating to work with someone slower than you are  
* Maintenance required, sustained pairing needs coaching and encouragement from leaders

## Chapter 8 - Workplace layout  

* People need to be able to sit comfortably side by side  
* If people need to move seat positions, then they possibly don't have a good view of the screen in the first place (you may want to address this)  
* Big focus on layout not costing any more money (not sure if I agree with this)  
* Kent Beck suggested Caves & Commons (big open area for working together, and small sound proof rooms for working on your own)  
* Effective pairs communicate every minute, thus more noise  
* Navigator should not point on the screen with their fingers cause it get paw prints on screen (use stylus instead)

## Chapter 9 - Pair rotation

* Concern that pair rotation creates generalist instead of specialists  
* Pair rotation may seem rigid and prescribed, in actuality it often occurs casually without formal schedule  
* Trust and strong bonds can be created as long as the rotating team is not larger than ten
* It is dangerous to have all knowledge in any area of the system known to only one person  
* Invaluable knowldege can be distributed through out the org just by people speaking to each other  
* Pair rotation can be used for training - move from a pull to a push (previously people had to ask if they didn't know something)  
* Suggestion to split a team between training and progress group, training group is aimed at helping people learning, progress group is aimed at progressing through the system  
* Suggested formular for Training Effor = Assimilation Time * (1 + Mentoring Time), survey showed training effort can be reuced by a factor of two through the use of pair programming  

## Chapter 10 - Other Issues to Consider

* How are performance apparaisals done, suggested peer review getting several people in the team to give feedback  
* Group size, pair programming scales in a way similar to the way solog programming scales, however pair rotation doesn't make sense if you rotate with 200 people. You never get to know things..., rather keep the group small 10-12 people. People can develop personal relationshps with teammates and the code can be understood by the entire group  
* Quality assurance (code review, design review, etc.), these may still be useful but pairing alleviates the need for many of these things  
* Functional & System Testing, pair in groups to test things  

## Chapter 11 - Tips n Tricks  

* Give the Driver some time to correct his/her own mistakes (a few seconds), especially with things like spelling etc.  
* If your partner or you are bored, drive
* If you are both bored, go for a brief walk and break the work up into small bits with frequent breaks  
* Start each paring session with a 'negotiation', basically explain the things that bug you when pairing and find out the things that bug him when pairing  

### Conflict in design

* as the navigator sees issues, write them on cards and them come back to them later
* try time boxed separations to explore different design approaches  
* sometimes just ask for 5 minutes to show the direction, and after that if there is still disagreement you can try the alternative  
* have someone (team leader / coach / manager) who resolves partner issues that cannot be resolved on their own  
* use a coding standard, this eliminates partner disagreement due to style
* test driven development works well with pairing
* Talk a lot, Talk about what you are doing. It helps your partner understand your logic
* If you don't understand what your partner is doing, then stop and ask. If you still don't understand, ask again. Ask until you understand
* "Trust me, it'll work" is not an acceptable answer when you ask a question  

~~~
There needs to be balance between holdings one's ground and compromise. 
Be assertive without being aggressive. 
A partner who always gives in to his or her partner's suggestion, is doing a great disservice to the team.
A partner who never gives in or never gives his or her partner's ideas a fair chance may as well not be pairing.
Pair's that insist on debating every single issue are impeding progress.
Choose your battles wisely; save them for issues that really matter
Practice active listening by acknowledging, restating, and summarizing ideas and discussion points
Be empathetic toward your partner
~~~

## Pair Programming Partner Picking Principles

I am combining these into smaller sections, this covers chapters 12 to 23

### Expert-Expert Pairing

#### Benefits 

* Get the most complex job done well
* Move fast  
* Experts bring different skills to the pair  
* Leads to well functioning integration  
* Experts learn from each other  

#### Challenges

* Management might feel it is overkill  
* Sometimes challenge is strong opinions  

### Expert-Average Pairing

Two types of average programmers... ones that are happy with being average, and others that are currently average but on their way to expert. 
Pairing an expert with average programmer that has no intention of improving is not effective.  
Pairing an expert with an average on the way up programmer is effective  
Recommend to first learn how to pair before learning tools, language, etc. Learning both at the same time can be ineffective.  

#### Benefits

* To get the average job done well, while raising the skill level of one of the pair  
* Average programmer has enough knowledge about the problem/tech/language to have a meaningful conversation  
* Expert can share tips and tricks to moving faster  

#### Challenges

* When average programmer has no intention to learn is a waste of the expert programmers time  
* Average programmer is not confident enough to ask the expert questions  

### Expert-Novice Pairing  

To get the easier job done well, while training a novice programmer  

#### Benefits  

* Novice accelerates learning by watching how an expert does things  
* The novice helps the expert do a better job just by being there and them having the explain what they are doing  
* Slows the expert down, which sometimes can be beneficial in helping expert think things through properly  

#### Challenges

* Requires the expert being able to interact with the novice  
* Expert needs attributes of patience, willingness to explain, and the ability to articulate clearly
* Novice can be too intimitated to ask questions which dramatically impacts learning  

### Novice-Novice Pairing  

To produce production code in a relatively noncomplex area of the project giving valuable experience to both programmers in the process  

#### Benefits

* Novices can help each other because they are working at the same pace  

#### Challenges

* Needs to be a coach available should the novices get stuck for too long  
* Easy for novices to go down the wrong path and "waste" time  

### Extrovert-Extrovert Pairing  

After long, thoughtful, constructive discussions, an excellent creative solution is created  

#### Benefits

* Often there will be lots of friendly banter
* Often openly questions decisions

#### Challenges

* Can be loud and full of laughter which may destract others  
* Easy to get side tracked into just general conversations  
* Some extroverts just can't stop talking never getting to actual code  

### Extrovert-Introvert Pairing  

To allow each partner to draw on his or her strengths and to improve upon his or her weaknesses  

**A lot of programmers are introverts**

#### Benefits

* When balanced contribution can be a good experience  

#### Challenges

* Each partner must give up a little to learn to pair together.  
* Extrovert must back off from talking all of the time
* Introvert must learn to speak up about whatever issue is at hand  
* Pairing will not work if both do not give a little  

### Introvert-Introvert Pairing  

Many programmers are introverted to some degree, there are no hard statistics on it but it is thought that the majority of programmers are of Meyers-Briggs personalit type INT (Keirsey 1998, Keirsey 2002)
Introverts can be fairly quiet and private.
Introverts are quick to listen and slow to speak.  
Extroverts are quick to speak and slow to listen.  

* Having two introverts solving a problem together can be really successful if you can overcome their natural tendency not to communicate with their partner.
* The natural intensity of introverts makes interaction a low priority. 
* Pairing an introvert with and introvert is a good way to start pair programming.  
* Introverts may find pairing with an extrovert overwhelming or find it hard to get a word in.  

#### Challenges

* Introverts can be very poor communicators  
* A lot of introverts would prefer to work on their own  

### Gender Nonissue  

Gender is not an issue. Challenges with pairing are based on personality types / flaws rather than gender.  
The one exception is gender disrepect.  

### Culture Nonissue  

Having pairs with different culrutal backgrounds is wonderful for building trust and communication within the team as long as there is communication the pair can succeed.
Focus on how to communicate effectively, be aware of accents that make communication harder.  

### The Professional Driver Problem  

Bad drivers:  
* Do not give up control of the keyboard  
* Unwilling to listen very much (or at all) to their partner

Be aware that:
* Some unconfident navigators may encourage their partner to stay by the keyboard all the time  

### My partner is a total loser and other excess ego problems  



### My partner is SO smart and other too little ego problems  

