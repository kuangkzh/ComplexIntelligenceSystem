# The Impossible Trinity of Complex Intelligent Systems

**This page is translated by ChatGPT.**

In the previous section, we outlined the origins of intelligence and introduced two types of intelligent systems with different causes. Aside from trivial intelligences like light, the value and difficulty of intelligence lie in its complexity. In this section, we will focus on the characteristics of complex intelligent systems.

**Definition**

A complex system satisfies the following assumptions:

1. The state space is extremely vast, and no individual can traverse all states completely.
2. Irreducibility: Complex systems consist of a large number of nonlinearly coupled components, and their evolutionary development cannot be fully described by low-degree-of-freedom equations.

In addition to these, for intelligence to emerge in complex systems, another important assumption must be met:

Locality assumption: Distance can be defined on the space composed of all states of the system at all times. There exist certain attributes and states such that the attribute undergoes linear changes in the neighborhood of this state in spacetime.

In simple terms, a portion of the system must exhibit differentiability in spacetime. On one hand, continuous variables with differentiability in space are learnable. Differentiability ensures that the values of variables in a certain locality, albeit not infinitesimal, are predictable, even if this predictability has errors. On the other hand, differentiability in time ensures that learning has generalizability. Even if intelligent agents selected from $P(s_{\pi,alive}^n)$ might have survived due to some luck, differentiability ensures that $P(s_{\pi,alive}^{n+1})$ also has a similar probability of survival or demise. This implies that patterns of past behaviors can be extrapolated into the future without issues.

It can be said that it is precisely locality that endows a kind of intelligence with genuine human understanding cognition, rather than merely being lucky enough to escape death.

However, this kind of promotional ability is limited. Machine learning theory tells us that given data, a model is either underfitting or overfitting. We directly substitute a $\phi$ native objective function and expected objective function into the Bias-Variance decomposition. Let $\hat{f}=S(s_{\phi}^n)$, $y=S_{\pi}(s_{\phi}^{n+1})=S_{\pi}(s_{\phi}^{n})+\varepsilon$, then we can obtain:

$\mathbb{E}_D \left[ (y-\hat{f})^2 \right] = \mathbf{Bias}_D (\hat{f})^2 + \mathbf{Var}_D (\hat{f}) + \sigma^2$

Here, $D$ represents the relevance distribution of the given $\pi$ and $\phi$ actual targets. As mentioned earlier, the relevance distribution can be described in terms of information interaction from an information perspective. In this definition, this equation regresses to its original meaning, where $D$ is the training set, $\hat{f}$ is the algorithm, and $y$ is the true data distribution. This equation implies that given a training set, regardless of the model chosen, its expected error is determined by bias, variance, and noise error as lower bounds. Typically, models can only seek a balance between high bias underfitting and high variance overfitting.

In this paper, we extend this impossible trinity trade-off to a broader range of systems. We can point out that for any intelligent agent, if it wants to achieve its own goals using some means or tools, when it decides on these means and expected goals, it also decides on the means' objective function and its own expected objective function, thereby falling into an impossible dilemma. High bias and low variance mean that the means are not implemented adequately, there is always a significant distance from the expected target, but it also means that the means may have stronger generalization ability. High variance and low bias mean that the means are implemented well, perfectly matching the expected target, but it also means that any future changes in reality may greatly affect the realization of the expected target. The only way to achieve both is to enhance $D$, but since the actual target is immeasurable, generally only the method of approximating the contrapositive proposition mentioned earlier can be used to sample and filter on as many state spaces as possible.

Therefore, we can say that any intelligence, when using tools, with a certain degree of coupling between the intelligent agent and the tool, either achieves good performance on observable indicators (low bias) or achieves good performance on unpredictable generalization (low variance). In any case, it faces the dilemma of choosing between underfitting and overfitting. This impossible trinity relationship exists widely in every intelligent system. Now let's move on to the relaxed examples.


## Market Decision Making: Information - Returns - Risk

When discussing the trade-off between indicator returns and generalization risk, the most direct analogy that comes to mind is the trade-off between returns and risk in investment decisions. In an ideal market, whenever we seek higher returns, we must bear greater risks. This trade-off is actually a special case of the underfitting-overfitting trade-off we mentioned earlier, because the pricing in an ideal market comes from sufficient competition after multi-party bargaining, and thus pricing in the short term always follows a normal distribution random fluctuation. In other words, the distribution of actual targets is completely unpredictable random normal distribution, and any investment portfolio would be overfitting.

If we want to increase returns while reducing risk simultaneously, the only feasible method is to have more information about the game behind the stochastic fluctuations in pricing. Without considering additional information, the expected profit from buying and selling in the ideal market is zero. Economists in reality can have a positive income expectation from trading because people can gain additional market information through prediction and analysis, thereby optimizing resource allocation through trading, and the income from capital flows is the profit from smoothing out information asymmetry. The expected returns and risks based on this additional information satisfy what we call the impossible trinity relationship.


## Social Allocation: Productivity - Efficiency - Equity

This is a more typical example, involving the intelligent role of humans, while the social system serves as a tool for humans to achieve the purpose of production and distribution. The same distribution system usually cannot simultaneously satisfy efficiency and equity. Typically, social operation efficiency has an explicit indicator, namely Pareto optimality, and the entire society operates around this goal. However, in reality, we also need to consider equity issues, namely the welfare and satisfaction of each individual, which is an unpredictable indicator (a generalization problem). Therefore, for humans, social systems always make trade-offs between overall operational efficiency and meeting the needs of each individual when it comes to distribution.

A way to address both challenges simultaneously is to increase productivity levels. For example, a certain system may flatten out the differences in individual needs by producing a large surplus of products, thereby increasing the coupling between the two at the final goal level. Alternatively, through information exchange, collecting the actual needs of each individual and establishing a fair and efficient distribution system, thus bridging the correlation between the two from an information perspective. In social allocation, productivity levels, distribution efficiency, and equity satisfy the impossible trinity relationship in this section.


## Evolution: r-K Selection

As the primary driving force behind intelligence, evolution naturally exhibits strategy differentiation between underfitting and overfitting.

The r-K selection is a hypothesis concerning biological evolutionary strategies, which categorizes organisms into two types based on their growth curves.

r (rate) strategy populations have high birth and death rates, short lifespans, small individuals, rapid reproduction, strong dispersal abilities, and adaptability to variable survival environments.

K (Kapazitätsgrenze) selection populations have population densities stable around the carrying capacity K of the environment. They have low birth rates, large body sizes, long lifespans, mechanisms for offspring protection, low dispersal abilities, and adaptation to stable living environments.

The r-K selection hypothesis has been criticized due to a lack of empirical evidence and being refuted by many counterexamples, such as large trees with long lifespans but strong reproductive capabilities.

However, we can still observe significant differences in biological classification between r and K selection. r selection, such as mice, cockroaches, microorganisms, reproduce almost without restriction, exhibiting strong propagation and environmental risk resistance capabilities. K selection, typical of humans, involves producing a small number of offspring throughout a lifetime and meticulously caring for and educating children, establishing a dominant position in stable environments.

Readers who have completed this section should realize that the ability to survive in stable environments and the ability to resist risks posed by environmental changes represent the two extremes of overfitting and underfitting mentioned in this section. Characteristics such as body size, lifespan, reproduction rate, and investment in offspring nurturing are means of achieving survival or risk resistance capabilities. Thus, a large-bodied, long-lived individual does not necessarily imply weak environmental adaptation ability, although it is highly probable, which is why the r-K selection hypothesis always finds counterexamples and is not suitable for universal application.

Nevertheless, we can still intuitively perceive from the r-K selection classification that there is no single strategy that can simultaneously possess existing survival capabilities and risk resistance capabilities. The previous dominant species on Earth, the dinosaurs, which represent K selection, could not foresee the day when a catastrophic disaster would affect the entire planet, directly shattering their formidable individual survival capabilities. r-selected organisms like cockroaches and other small creatures, however, continue to survive through strong reproductive capabilities and genetic mutations, with some individuals surviving mass extinctions, persisting until today. However, they also could not foresee that, with humans' pursuit of individually powerful deep-search routes, when the understanding of the environment and offspring education reach a limit, there would be a discontinuous leap in biological survival capabilities, leading to a new generation of Earth's dominators.

So, what humans cannot foresee could be highly-coupled single-point risks (such as viruses) or risks of self-destruction after the evolution of technology and consciousness?
