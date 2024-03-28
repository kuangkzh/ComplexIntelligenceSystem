# Building Intelligence - Alignment: Providing Optimization Directions

**This page is translated by ChatGPT.**

As mentioned earlier, the fundamental reason why intelligent systems fail to meet expectations lies in the existence of a gap between instrumental goals and actual goals, leading to goal misalignment.

Whenever we select an object as a tool, we effectively determine the goal state distribution of that tool, which is a fundamental attribute of everything. For the tool, it only follows its own developmental rules, constantly progressing towards the set goal. However, it can never fully comprehend the actual goals of the user, thus there always exists a gap between the tool and the user.

The question this section aims to explore is what kind of general construction techniques can be used to align the goals of both parties.


## Sampling

Free evolution is undoubtedly the best solution for aligning instrumental goals with actual goals because evolution randomly samples from the entire space. As long as the sampling scheme is sufficiently random, the goal will not be biased towards any particular local state space. Therefore, evolutionary algorithms typically exhibit strong robustness.

This is also why economic entities born in a free market are more competitive than those in a planned economy. The former operates around the ultimate goal of survival, while the latter operates around planned objectives. However, there still exists a gap between planning and the ultimate goal. At least in the past 50 years, the efficiency brought by planning has not been able to compensate for the generalization risks introduced by goal differences.

However, evolutionary methods are usually not applicable to most systems. The premise of global sampling is that we can afford the high cost of operating such a system. In a free market economy, sampling is not entirely random; individuals are more like stabilizing through annealing within randomly initialized points. In deep learning, we sample in the hypothesis space, usually randomly sampling in a Gaussian distribution space, then encoding the sampled points into textual or image data, or around some known samples, augmenting data through some prior properties.

But if the sampling method is biased, the intelligence learned through sampling will have a greater risk of bias.


## Pooling

Pooling is a feature extraction method that downsamples data by computing some statistical value over intervals as interval features instead of the original data. Pooling not only reduces the computational burden and parameter count of the model but also helps prevent model overfitting.

Pooling is effective because real data generally exhibits a certain property: 

- At large scales, the overall low-frequency statistical features of the data usually have little variability and contain little information.
- At small scales, high-frequency features of the data are often influenced by various noise fluctuations and contain noisy information.

Therefore, aggregating details at a moderate scale can not only acquire genuinely useful information but also be less susceptible to noise effects, while also reducing the required computational resources.

Various pooling mechanisms exist in the human body. In auditory perception, loud sounds can mask softer ones. In vision, the colors perceived by the human eye are actually combinations of the total values excited by different wavelength light on the cones. In human society, the most typical example of pooling is the voting system.

When considering the needs of all individuals, it's clearly impossible to survey each person's opinion one by one. The voice of the crowd is always very noisy. Hence, we conduct voting to filter out the most prominent features from the group. More complex voting systems are hierarchical, with each level selecting the most prominent ideas as representatives and participating in the next level of voting.

If only one large-scale national vote is conducted, when there are many people, those small but valuable voices are easily overwhelmed.


## Flattening

Residual connections, as a fundamental module, have become an indispensable foundation in modern deep learning. Flattening management has also become a management model pursued by modern large enterprises, aiming to increase management efficiency by reducing management levels and adding cross-level management.

This means that within a large intelligent system, the distortion of the system's own goals can also become a major factor affecting system performance. In a multi-level intelligent system, the top-level system actually functions using the lower-level systems as tools. Thus, there is a new gap between the tools and the actual goals of the top level, and the more hierarchical the system, the greater this target deviation.

Even in strongly coupled systems with powerful goal propagation capabilities like neural networks, the accumulation of target deviations layer by layer can make it impossible to train deep networks. Therefore, in multi-level systems, there must be some mechanism to connect the upper and lower levels, ensuring that the goals are aligned at least within the system.


## Contrastive Learning

In the real world, we are usually not interested in, nor can we easily understand, all the details of something. Instead, we are more concerned with certain attributes it exhibits and its correlations with other things. More importantly, similar things often share many common attributes, and most of these attributes are unimportant to our ultimate goals. Only the differences are crucial.

Therefore, exploring associations and contrasts between similar things often helps us focus on the true objectives.

Most pre-training tasks aim to memorize a sample completely, which is often useful in the early stages of model initialization because pre-training on a large amount of data helps the model learn the commonalities among similar data. However, when the model needs targeted training for specific tasks, continuing to use pre-training tasks is like asking students to memorize answers when learning math problems, which is clearly an inefficient way of learning. Either students can only learn the superficial appearance of solving problems, or they need to memorize thousands of questions of the same type. One of the main reasons why many students perform poorly in math is that they keep trying to memorize the correct answers and expect to find certain keywords and templates from the answers to apply to new questions, which is exactly the same as SFT overfitting in LLMs.

A healthy learning approach should strive to eliminate irrelevant evolutionary directions from the goal. For example, in the case of math problems, if students continually compare the differences between the correct solution and their own incorrect solutions, they can gradually grasp the correct problem-solving approach. Other content in the questions, such as grammar and tone, are unimportant and can be eliminated through comparison.


## Reinforcement Learning

Reinforcement learning is a particular form of comparative learning. It defines a reward function and aims for the model to perform well on this final reward, which is the attribute relationship that reinforcement learning focuses on. However, the final reward is not continuous, so reinforcement learning always needs to adopt some method, such as sampling or value networks, to smoothly align the final goal with the goals of each step of the model.

As mentioned earlier, solving math problems is such a process. The ultimate reward for problem-solving is simply right or wrong, but by comparing each step of the problem-solving process, we can gradually find the correct solution process. This is where our internal value network comes into play.

It can be seen that the strength of reinforcement learning lies in its ability to actively align goals through some mechanism, while other learning methods rely on manually aligning goals based on prior assumptions. Such a model comes with a value layer that is highly aligned with the ultimate reward goal, and since the value layer is highly coupled with the action layer, its goals can be passed down almost without loss.

Therefore, through reinforcement learning and human feedback, we can create such powerful artificial intelligence. However, alignment in OpenAI goes beyond reinforcement learning. From technical reports, it can be seen that the development team of ChatGPT stays aligned with the annotation team, and the data annotation of the annotation team aligns with the goals of ChatGPT. Each of these steps is essentially a form of reinforcement learning for goal alignment, ensuring that the model remains highly aligned with the team's ultimate goals.

The essence of alignment lies in increasing coupling and information exchange, which is a costly endeavor. Assuming there are three layers: the ultimate goal, the value layer, and the action layer, with a cost of transmitting each unit of information as \( a \) for the first two layers and \( b \) for the latter two layers, there should exist an alignment method that maximizes efficiency. I conjecture that the amount of information transmitted for the first two layers should be $\log_{ab}{b}$, and for the latter two layers, it should be $\log_{ab}{a}$. (This conclusion is only a conjecture, with no derivation process, solely based on mathematical intuition.)

The risk in reinforcement learning still lies in goal distortion. Firstly, the reward function artificially set by humans does not represent the human's ultimate goal, and there will always be a gap between the value layer and both the reward function and the action layer. As deduced in the first chapter, besides increasing the coupling of intelligence with tools (information exchange, datasets), it's always impossible to simultaneously optimize both the visible and invisible parts of the goal.



## Adversarial Learning

Adversarial learning is a special type of reinforcement learning that also employs the structure of value networks and action networks. However, in adversarial learning, the value network approximates a new alignment target using the method of contraposition, and then the action network is required to align with the contrapositive approximation of this original target. Adversarial learning is effective because when the question of what the target is becomes sufficiently complex, solving its contrapositive is often simpler than solving it directly. This is because the contrapositive of the target is a judgment problem of whether the target has been achieved, and the proposition itself is often a generative problem, much like the relationship between P and NP.

In image generation, GANs approximate the target proposition of generating real images by judging whether generated images are indistinguishable from real images, and then instruct the generator to generate images that are sufficient to confuse the discriminator. In the real world, we also construct adversarial systems. When we want to produce something, we first establish corresponding quality inspection systems. Industries such as food, medicine, phones, and chips all have a set of industry quality inspection rules, and for producers, they are in a constant adversarial relationship with these rules. When constructing deep learning models, the models are also in an adversarial relationship with our quality inspection standards (validation sets).

However, the problem with adversarial learning lies in the fact that the reason contrapositive approximation is simpler is that its feasible solution space is much larger. Achieving complete coverage of the solution space is as difficult as with the original proposition. Therefore, the discriminator only achieves a weakened solution of the contrapositive. In this incompletely covered solution space, powerful generators often find shortcuts to escape, much like unscrupulous businesses evading regulations to sell counterfeit products and LLMs generating illusions.



## Multi-Objective Learning

The traditional view holds that since various parts of the world are generally interconnected, setting multiple objectives for a model to learn together helps in understanding the connections between various problems, allowing cognitive understanding of the world to be shared among different problems. Using the theory explained in this article, when an agent has multiple objectives, that is, when it has a symbiotic relationship with multiple different intelligences $ P(s_{\phi,alive}^n | s_{\pi}^t s_{\phi}^t s_{\pi,alive}^n) \gt P(s_{\phi,alive}^n | s_{\pi}^t s_{\phi}^t) $, under the constraints of various objectives, the agent's objectives are not easily biased towards one side and overfitting is reduced. Consequently, the probability of achieving actual objectives is increased, and thus various tasks related to it can also benefit from this improvement.

When there are enough tasks, the agent can achieve dynamic balance in the game of multiple objectives, enhancing coupling with the world while reducing bias and variance. In the first chapter on the principles of intelligence, we used the example of humans using knives to illustrate the relationship of equality and mutual utilization between intelligence and tools. However, astute readers should notice that the status of humans and knives in this example is extremely unequal; the selectivity of knives towards humans is much lower than that of humans towards knives. This is because the purpose of knives comes from human usage, while for humans, using knives is just one of their many purposes. We will delve deeper into this relationship in Chapter Three.

For any form of intelligence to become "true intelligence" in the eyes of people, it must pass through the constraints of multiple objectives. Otherwise, it is prone to be hijacked by a single objective and may eventually decline amidst unforeseen risks. A society must be governed by various government agencies and public organizations restraining each other, and a healthy market must be stabilized by multiple parties engaging in strategic bargaining to set prices. Otherwise, it is easy to drift towards a monopoly of power, ultimately leading to overfitting guided by a single objective until decline.


## Summary

The main focus of this chapter is to provide examples based on the foundation laid in the first chapter, with the aim of cultivating intuitive thinking in readers within the framework of the new theory. Through the analysis and examples in these two chapters, readers should have developed the ability to proficiently analyze an intelligent system. They should be able to quickly identify the goals and expected objectives of a system, analyze its performance under underfitting and overfitting conditions, and, based on the impossibility triangle theory, identify reasons why the system cannot achieve both objectives simultaneously, while also being able to provide optimization recommendations.