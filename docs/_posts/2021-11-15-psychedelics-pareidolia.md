---
layout: post
title:  "What do psychedelics do on the algorithmic level? The case of pareidolia"
---
Psychedelics change perception strongly and in the structured way. We also know which receptors they affect (and some of them, like LSD are quite specific - the seem to affect only one receptor - 5-HT2A).

If only one receptor can change the perception and actions so much, looking at psychedelics can be a good approach to understand how the brain works.

For example, [Qualia Research Insititute](https://www.qualiaresearchinstitute.org/) are taking the potential of psychedelics to understand consciousness very seriously  and[ it's super interesting to follow their research](https://qualiacomputing.com/2016/12/12/the-hyperbolic-geometry-of-dmt-experiences/).

As one small case, I wanna speculate about what exactly psychedelics might change in the brain computations looking at the phenomenon of enhanced pareidolia during tripping.

## What is pareidolia?
Pareidolia is the ability to see faces or objects in some sensory input that is not this object: seeing creatures in cloud, smirking face in the wall (dogs in a muffin??). This of course is happening without psychedelics, but they enhance this effect.

![](https://cbsnews1.cbsistatic.com/hub/i/2014/05/06/7abc78fd-0134-4fe2-a466-1cbbb48790a8/ebay-virgin-mary-grilled-cheese-getty-128167414.jpg)
<p style="text-align: center;" markdown="1">Famous case</p>


Pareidolia can occur not only in  the visual domain, but in auditory too. This is well described by Steven Lehar [in his book](http://cns-alumni.bu.edu/~slehar/GrandIllusion.pdf):

  _At one point three of us stopped by a babbling brook that was crashing and burbling through the rocks down the steep mountain slope. We sat in silent contemplation at this primal “white noise” sound, when Lonce commented that if you listen, you can hear a million different sounds hidden in that noise. And sure enough when I listened, I heard laughing voices and honking car horns and shrieking crashes and jangly music and every other possible sound, all at the same time superimposed on each other in a chaotic jumbled mass. It was the auditory equivalent of what we were seeing visually, the mind was latching onto the raw sensory experience not so much to view it as it really is, but to conjure up random patterns from deep within our sensory memory and to match those images to the current sensory input. And now I could see the more general concept. We experience the world by way of these images conjured up in our minds._ 
  
This phenomenon of the visual system makes sense from the evolutionary perspective: often the predators are well hidden and camouflaged, but if you can break the camouflage and can recognize the shape of the tiger body that is almost indistinguishable from the jungle background, you have an evolutionary advantage.


## How can pareidolia be explained on the algorithmic level

What does it even mean when we say, "I see a face"? One of the simplest models that are used in artificial neural nets is that the brain has feature detectors (in the case of the face there can be the detector of the mouth, eyebrows, etc). These features are weighted-summed and when the threshold of this weighted sum is reached, we say: faace!

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FUL5JXKlKr4.jpg?alt=media&token=0647a13a-42f5-4cd8-9cd3-1ecc6fad9bd1)

Now, if we follow this super simple model, then during enhanced pareidolia condition, detectors for the intermediate-level features of the face (eyes, mouth, etc) get activated more strongly so that the threshold for recognition of the face is reached more easily. Something like "oh this crack on the wall is the mouth!" means that the "mouth" feature is activated more compared to the situation "nah this is just a crack".

Notice that during pareidolia the excessive activation of certain featuers (face parts) doesn't prohibit activation of other features, rather than more features get activated for the given sensory input. Compare: 1) "this is a crack" - "crack" feature is activated. 2) "this is a crack and it is a mouth" - both "crack" and "mouth" feature is activated.

Why could these intermediate neurons be activated more strongly during enhanced pareidolia? (again, assuming that the model "detection of face features-> threshold" is correct) There can be at least two perspectives.

### Predictive Processing perspective:

Hierarchical predictive processing model (e.g. the one presented in [Bogacz 2017](https://www.sciencedirect.com/science/article/pii/S0022249615000759)) says that in some intermediate level of processing hierarchy the activation of a neuron (or an assembly of neurons) representing a particular feature is something between the prediction about the value of this feature from higher levels (top-down input, \(v_p\)) and the representation from the lower levels of hierarchy (bottom-up input, $$u$$). One can imagine that representation from the higher level and representation from the lower level pull the neuron in the intermediate level to different sides and as a result, the activity of this neuron settles in a somewhat average activity between the two.

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FacIy1R7Gb1.jpeg?alt=media&token=dc361377-e38c-4ba3-b952-2bb872c4c1ad)
<p style="text-align: center;">Hierarchical predictive processing model from Bogacz 2017</p>
If $$phi$$ here is the feature coding for some face part, then if in pareidolia this neuron fires stronger, it can be either because the bottom-up input got stronger or the top-down input became stronger. Increasing the bottom-up input seems less possible to me because it is constrained by the input from the retina while modifying top-down input (e.g. the belief that you should see a face here?) seems more plausible.

Note: By "increasing top-down input" I mean that alterations in top-down input can happen anywhere along the way: $$v_p$$ can be increased, or the synaptic weights between $$v_p$$ and the prediction error neuron epsilon_p can be increased, or synaptic weight between epsilon_p and phi can be increased.

### Backpropagation-activated calcium firing (BAC firing) perspective

Another way to look at the firing of the "face part" neurons is through the idea of coincidence detectors and their implementation via Larkum's backpropagation-activated firing (BAC firing) mechanism.

The coincidence detection model means that every coincidence detector (neuron representing some feature) receives two types of signals:

1. bottom-up, carrying the information from the lower layers (retina in the extreme case) that this feature is present in the environment

2. top-down input, carrying the belief that this feature should be present based on some broad context (e.g. I am in the airport so that moving dots in the sky are more likely to be interpreted as the airplanes so that the context will provide a stronger top-down signal to the neurons representing airplanes)

Coincidence detector fires only when both of these inputs are present, but not when either of them (essentially, it is AND gate).

BAC firing is the neuronal implementation of the coincidence detector between the bottom-up input and the top-down input coming to the neuron-coincidence detector:

If we look at the cortical excitatory neurons, and especially layer 5 neurons, we will see that they have 2 compartments: somatic, with the basal dendrites, and the apical compartment with its distal apical dendrites. 

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2F69cyihmM32.png?alt=media&token=144a1ebe-4e4d-4078-a97e-05499d1a238d)
<p style="text-align: center;" markdown="1">[Lederberger and Larkum 2010](https://www.jneurosci.org/content/30/39/13031.long)</p>
            
By patching simultaneously dendrites and soma of layer 5 pyramidal neurons, it was shown that:

- If you provide the excitatory input only to the basal dendrites, neuron will fire very modestly.
- If you provide the input of the same strength only to the apical dendrites, there won't be any firing at all.
- However, if you simultaneously activate basal dendrites with a very slight input to the apical dendrites, there will be a massive burst firing.

This happens because the modest firing due to basal dendrites leads to the Na+ action potential backpropagating from soma to the apical dendrites, the apical trunk is depolarized and it becomes way easier for any apical input to trigger Ca2+ spike propagating to the soma and trigger the burst of spikes.

This is the illustration of this behavior from the Larkum 2013 review:

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FKHMj-ixnSU.png?alt=media&token=07694197-6184-439f-9da2-09b4531a071c)
<p style="text-align: center;" markdown="1">[Larkum 2013](https://www.sciencedirect.com/science/article/pii/S0166223612002032?casa_token=J3ypBevvwooAAAAA:GwHpid9Ez4RUs1TAzAyu0isn7obIX3P2Du1hrVDUMr1aJn8NZAEfLDd-WgvQA1qWeHtZ6NAyJmsm)</p>


Importantly, from this mechanism we can see that coupling between this compartment can be modulated: the membrane potential of the dendritic trunk can be moved closer or further from the threshold potential (e.g. by opening/closing Na+ and K+ channels along the dendritic trunk) so the contribution from the top-down input to the firing of this neuron can be also increased or decreased.

Assuming that the sensory, bottom-up input is coming to the basal dendrites and top-down input is coming to the distal apical dendrites, we get the coincidence detector whose characteristics can be modified by changing coupling between compartments!

Thus, according to this mechanism, during enhanced pareidolia, neuron representing a face part might be firing stronger exactly because the coupling is increased, the specificity of the coincidence detector is decreased and now the face part neuron is firing even when the top-down input is small, given that the corresponding bottom-up input is also provided.

## What do psychedelics have to do with it?

These two perspectives allow us to speculate which parts of the cortical circuit are changed by psychedelics and how they can increase pareidolic experiences.

### Predictive processing

As it follows from the model, to activate representation neurons more strongly we can either increase sensory input, or increase the strength of the predictory projection v_p synapsing onto the prediction error neuron epsilon_p for its corresponding representation neuron phi, or we can increase any synaptic weights in both bottom-up and top-down connections leading to the given representation neuron. Psychedelics might increase any of these properties.

### BAC firing

Psychedelics mainly act on 5-HT2A serotonergic receptors. If we look at where in neurons these receptors are expressed, then we will see that they accurately land along the apical trunk! As authors of [Jakab and Goldman-Rakic 1998](https://www.pnas.org/content/95/2/735.long) put it: 

_The majority of the receptor-labeled cells were pyramidal neurons and the most intense immunolabeling was consistently confined to their parallelly aligned proximal apical dendrites that formed two intensely stained bands above and below layer IV._

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2Fvnpgoe_R7Z.png?alt=media&token=d437acf9-7d06-4749-b878-c12369dc0977)
<p style="text-align: center;" markdown="1">[Jakab and Goldman-Rakic 1998](https://www.pnas.org/content/95/2/735.long), Figure 1</p>

So what might be happening is that psychedelics increase the coupling between somatic and apical compartment of a neuron by moving the membrane potential of the dendritic trunk closer to the threshold potential, so that now if bottom-up input (sensory stimulus, cracks on the wall) and top-down input (feedback, belief that you should see a face??) match, this neuron fires stronger than in the sober case.

The claim that psychedelics increase the influence of the feedback input coming to layer 1 on the neuron's firing is consistent with [Aghajanian and Marek 1997](https://www.sciencedirect.com/science/article/pii/S0028390897000518?via%3Dihub) experiments: they stimulated layer 1, patched soma of layer 5 neurons, and recorded EPSPs. When they applied DOI (analog of LSD), they saw an increase in EPSPs compared to sober neurons.

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FFfX70vmPXJ.png?alt=media&token=a080bf0f-3fd1-4395-9b33-f8bc519f44e5)
<p style="text-align: center;" markdown="1">[Aghajanian and Marek 1997](https://www.sciencedirect.com/science/article/pii/S0028390897000518?via%3Dihub), Figure 8</p>


So, overall,  the pareidolic process might be looking something like this: 

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fspindle%2FqLBFkkSWjr.jpg?alt=media&token=57df8e9a-0b9e-4be8-b7b1-31f56a8e916a)
<p style="text-align: center;" markdown="1">Blotter - courtesy of CAT TRIP Telegram stickerpack</p>


Assume that two alternative hypotheses are active initially: that you might see a car and the face in the wall. They send their feedback/context projections to the apical dendrites of neurons of their lower layer features, but only a subset of features also receives the sensory input to their basal dendrites (because only some features are compatible with the sensory input), assume it is only f1, f3, f4, and f5. Only f1, f3, and f4 receive both apical and basal inputs, but in the sober state, it still wouldn't be enough to strongly excite these neurons. On psychedelics, all of these neurons might be activated way stronger because of the increased coupling. But because more features are activated for the face features, than for car features, only the representation for the face gets activated. This might in turn increase the strength of feedback projections back to the face features, face features get activated even stronger, so there can be several iterations during which the visual system becomes more and more sure that it sees the face.

What this speculation doesn't explain is if the coupling is increased uniformly for all representation neurons (and I don't see why it should be increased nonuniformly), then why are the representation neurons for the face or creatures parts activated more strongly than others? In other words, why do we see faces in the walls more often than other objects? Is it about the saliency and importance of these stimuli for humans? Or the overrepresentation of this type of data in the human memory (i.e. we see faces every day more often than any other type of objects?), or that the spatial structure of the patterns where we see the faces (pecky wall) matches well the spatial structure of the face, and in some other types of patterns it is easier to see other types of objects (an argument in favor of this is that in clouds for me it is more likely to see some giant floating creature than some face)? 

In any case, it's only the small fraction of things that psychedelics are doing and it would be cool to figure out how they cause plenty of other effects.
