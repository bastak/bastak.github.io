Status: raw post, more like a stream of consciousness

inspired by https://twitter.com/nickcammarata/status/1381685410263400456?s=20&t=9kyB8iky3NgBzu_RZc4hLg

If we imagine the cortex as the machine that finds patterns in patterns and predicts more and more sensory consequences as it runs, the important engineering problem when designing such a machine is to create a mechanism that knows when it’s the right moment to halt the machine, to stop searching for patterns in patterns, and predict consequences. 

Too early is bad because it leads to underfitting. Bad because based on the modeled consequences the organism will select the action which will have bad consequences (e.g. say smth in the conversation that will hurt another person because you didn’t run the predictive machine for long enough to realize that it will hurt). 

Running it for too long and thinking too much about what could be the consequences of some conversation is also bad because it leads to overfitting and selecting the action which will be based on the modeled consequences which are totally off from reality because with the limited data you can’t predict that well into future, but you still force the predictive machine to do it. So it's important to understand when to stop.

One implementation for such halting mechanism could be to have the system consisting of two subsystems: predictive machine and the controller that outputs the binary signal: "on" or "off", and whether it’s on or off depends on many other inputs to this controller: the importance value, some measure based on the outputs of the predictive machine (e.g the ones that estimate how overfitted or underfitted the predictions are: e.g. if the predictions become too elaborate or protrude too much into the future it forces the controller to output off signal).

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FflMAChye-W.png?alt=media&token=310a503a-b4c6-4fcc-9858-d1c5ab12cd64)

So in the case of overthinking the “importance of the topic” signal to the controller is so high that it overwhelms the off drive coming from the measure signaling overfitting and the predictive machine runs way longer than it would be normally.

Reckless optimism, inversely, would be the controller that is biased to halt the predictive machine too early saying “nah everything will be alright” failing to actually think the consequences through.
 
For further digging into how it might be implemented in the brain: maybe [noradrenaline has something to do with it?](https://www.sciencedirect.com/science/article/pii/S0896627312008197?via%3Dihub)
