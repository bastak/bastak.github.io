---
layout: post
title:  "Three types of comparators for action selection"
---

{% include math.html %}

_It is not useful to know what will happen. What is useful is to know what might happen, depending on what you do. If there is nothing you can do about the future, what is the functional use of predicting it? So what is useful is to predict the future conditionally to a different set of potential actions. This is about manipulating models of the world, not representing the present._
<p style="text-align: right;" markdown="1">[Romain Brette](http://romainbrette.fr/a-brief-critique-of-predictive-coding/)</p>

### Couple of clarifying notes
1. I try to give the examples which served me as the source for some thought/generalization and if you notice that you don't agree with my jump from the example to the generalization - let me know! It can be the start of the discussion - what I am missing, why it doesn't work like this, what could be the better model etc.
2. Also, I will be trying to do claims that are [more precise at the expense of correctness](http://paulgraham.com/useful.html) so it is easier to disagree and to focus the discussion on the mechanistic details of the model/concept.

What is the main computational problem that the brain solves?

Of course, the brain does many different things and solves many computational problems, like object identification, movement, navigation, etc. However some functions of the brain are the means for solving a larger computational problem. 

For example, the brain solves the problem of edge detection but this solution is not the final objective. It is the means for solving the larger problem - object detection. The same goes for the solutions of bigger problems, like representation of the environment: the brain doesn't just want to represent the environment as accurately as possible for the sake of the good representations, rather it is a part of the solution for some larger problem.

In other words, if we were to set up the hierarchy of the problems that the brain solves, what would be on top?

On the very top is probably the reproduction: remained only the organisms that reproduce well. To reproduce well it is necessary to at least survive for a while. So survival I would put directly below.

But what could be directly below the reproduction and survival?

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FU1PjlosMBM.jpg?alt=media&token=32ffea37-6071-4003-a251-32c25f5287da)
<p style="text-align: center;" markdown="1">Hierarchical tree of the computational problems that the organism has to solve</p>

My current guess after reading [a great paper from Paul Cisek](https://link.springer.com/content/pdf/10.3758/s13414-019-01760-1.pdf) is that it is the problem of keeping the set of important variables at their optimal values - **setpoints** and directly below in this hierarchy - the problem of action selection that solves the problem of keeping the variables at these setpoints.

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FD_fQF3Gab2.jpg?alt=media&token=df5e7caa-f776-45cb-bd9c-14db5427f875)

What do I mean by this?

In his paper, Cisek proposes to consider any organism as a set of negative feedback controllers.

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FpyaFc_GhqT.png?alt=media&token=bbf4b4a3-caf6-469b-9c4b-d31381e0ffd7)
 <p style="text-align: center;" markdown="1">Figure from [Cisek paper](https://link.springer.com/content/pdf/10.3758/s13414-019-01760-1.pdf) illustrating the idea of negative feedback controllers.</p>
 
The main idea is that the organism wants to maximize its survival chances. (if we ignore for now the cases where reaching the goal of reproductive success clashes with the survival goal). However the chances of survival is an intractable entity: the organism cannot directly compute which states have high survival chances and which - low. Instead, the organism tries to keep the set of certain (more computable!) variables at their optimal values (setpoints) because keeping these variables at their setpoints correlates really well with survival. For example, keeping the concentration of ions in the body at a certain level, not having a face of a lion in your visual field, etc.   

When one of these variables deviates from its setpoint, the brain turns on the complex machinery (negative feedback controller) to bring this variable closer to its setpoint. This machinery is called **the action selection mechanism**.

The goal of this post is to describe really coarsely the potential scheme for such an action selection mechanism that requires 3 types of comparators: circuits that compare the values of two inputs and become active if these input values coincide ("match comparator") or don't coincide ("mismatch comparator").

So, which components might we need to select a good action that really brings the deviated variable closer to its setpoint?


### Step 1

Let's denote with $$V$$ our deviated variable. 

For the whole mechanism to work, we need to be able to detect the deviation of $$V$$ in the first place. Let's introduce *the first type of comparator*. Its first input is **the actual value of this variable**  at time t: $$V = v_i^{(t)}$$, which is being measured with internal or external sensors, for example, the current taste of salt, [borrowing the example of Steve Byrnes](https://www.lesswrong.com/posts/wcNEXDHowiWkRxDNv/inner-alignment-in-salt-starved-rats). The second input - **the desired value** $$V = v_{set}$$ - e.g. the desired feeling of saltiness on the tongue[^1].

This type of comparator should be a mismatch comparator that gets active when the deviation is sensed as we want this signal to be salient and available to other circuits.

Nothing prohibits it from being a match comparator too, if the downstream reader circuits will interpret the signal from this comparator inversely, but it causes some problems, like the waste of energy when all the variables are at theirs setpoints and these neurons will be firing constantly.

The signal about the deviation from this comparator should trigger the action proposal mechanism to correct the deviation.

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FSFAp8a0ACf.jpg?alt=media&token=96588419-9f2d-407a-acdb-63cd10323f54)


### Step 2

This magical mechanism proposes several candidates-actions to choose from. (check out the cool [sequence of posts from Kaj Sotala](https://www.lesswrong.com/s/ZbmRyDN8TCpBTZSip) for the potential model of such action proposal and selection mechanism in the framework of Internal Family Systems)[^2].

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FJcwAN6180T.jpg?alt=media&token=ce025dd7-b974-4bce-8e3d-62f1285644b1)


### Step 3

In such mechanism there is one design choice: If we have several candidates-actions, how do we decide which one is the most desirable in the current situation, what is the criterion by which we choose the action? One simple criterion is the following: the action that brings the deviated variable $$V$$ closest to its setpoint (compared to other candidates-actions) should be selected.

To understand which action brings $$V$$ closest to its setpoint, the brain might be utilizing the **forward model** - function (e.g. implemented with a synaptic weight matrix) that predicts the sensory input: what will be the value of our variable $$V = \tilde{v_{a_i}}$$ if a given action $$a_i$$ is taken. For example, the well-learned model predicts that if I lick a pretzel, I will experience a strong taste of salt on my tongue.

So for every proposed action $$a_i$$  the forward model is run and the corresponding prediction for the next timepoint $$\tilde{v}_{a_i}^{(t+1)}$$ for the variable $$V$$ is computed[^3]. 

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2F1GSykM4kpK.jpg?alt=media&token=dc7ed079-493a-4d13-a642-af55f7a1f426)


### Step 4

Here is where *the second type of comparator* appears. It is the key element in the system which chooses the action. For every proposed action it compares the **predicted value of the variable** (predicted with forward model for the given action) with the **desired value**. The action corresponding to the comparator that is most active is finally magically selected (because the corresponding action brings the system to the setpoint most effectively), implemented and the process is repeated. 

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2F3nK_lWVLfu.jpg?alt=media&token=625c6c94-fafb-4729-9db8-91e594da9335)

I assume that if these comparators even exist, they are more likely to be match comparators, because the action that is the closest to the desired input should be the salient signal. [BAC firing](https://bastak.github.io/2021/11/15/psychedelics-pareidolia.html) could be one implementation of such comparator. And speculating further, if these action selection comparators are the subset of the excitatory cortical neurons (which have these nice properties of match comparator) in the e.g. visual cortex, then it is funny to think that the firing of these neurons is not needed to represent visual stimuli at all (it is already known that firing of many neurons in the visual cortex poorly reflects the visual stimuli,  rather [they are correlated with movements](https://www.nature.com/articles/s41586-019-1346-5)), but instead it helps to select the action that will lead to the desired (in the current second) visual input.

If we consider the problem of capturing the prey and the organism wants to keep the prey all the time in the center of the visual field, then the correct choice between "turn left" or "turn right" is different every second (i.e. setpoint is dynamical, prey is to the left or to the right) and there is no way the action selection mechanism can know which action to choose without the help of the visual cortex! However i

The *third type of comparator* appears if we start to get concerned about how the forward model is learned. One possible implementation is the predictive processing module: there the key element is the prediction error neuron: mismatch comparator that receives **the predictions about the variable** $$V$$ from the forward model and **the actual value of** $$V$$ in the next time point. If the prediction and the actual value are different, the prediction error neuron fires, this signal goes to the forward model and magically updates it so that better predictions of $$V$$ for the given action are generated in the future.

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FAfdH5uEp_s.jpg?alt=media&token=1c670360-df5f-4f89-80dc-05b195330779)

To sum up, here is how these three comparators differ from each other in terms of inputs and match/mismatch type:

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FMPMTPtaJ3J.jpg?alt=media&token=303bd201-ebd7-4ebc-a3d1-2818ea0e049e)

This is the simplest architecture that I can imagine which implements such a negative feedback controller. I would be happy to know which aspects of this model are contradicted or supported by experimental data.


### Footnotes

[^1]: It is interesting to think about the properties of such setpoints, for example, they for sure should be dynamic: sometimes you want to feel a lot of salt on your tongue, when you are salt deprived, but if you've just eaten the ton of chips, you would be rather appalled by it, so the desired feeling of saltiness should change depending on the context. It’s interesting to ponder how such flexibility of the setpoints can be implemented.

[^2]: Here the assumption is that the only possibility is to propose the set of actions and the organism can only choose among them. However, the real organisms can also decide to enrich the set of available actions instead of just choosing from the plate. How this is happening is a separate question (e.g. instead of choosing between eating the remnants of food (exploitation) or going foraging (exploration) I can create an entirely different strategy - to go and cultivate crops)

[^3]: When I was drawing the diagram, I got confused if it is more correct to draw one forward model and every action utilizes the same model or if every action has its own forward model (the final version). Having separate models sounds implausible because if we model the forward model with the weight matrix, then we would have to copy this matrix as many times as we have actions which would be a massive waste of space and energy. From another side, if we have one forward model and for all actions predictions are estimated in parallel, we get screwed up predictions because of the several simultaneous inputs to the same weight matrix: if we need $$Ma_1 = v_1$$, but we have several simultaneous inputs, then $$M(a_1 + a_2) = v_1 + v_2 \neq v_1$$. So either the assumption that consequences for several potential actions are estimated in parallel is wrong, or that the output from the forward model is somehow magically demixed, or the whole mechanism is completely different.
