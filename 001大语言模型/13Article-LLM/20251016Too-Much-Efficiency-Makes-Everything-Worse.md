## 20251016Too-Much-Efficiency-Makes-Everything-Worse

[Too much efficiency makes everything worse: overfitting and the strong version of Goodhart’s law | Jascha’s blog](https://sohl-dickstein.github.io/2022/11/06/strong-Goodhart.html)

Increased efficiency can sometimes, counterintuitively, lead to worse outcomes. This is true almost everywhere. We will name this phenomenon the strong version of Goodhart's law. As one example, more efficient centralized tracking of student progress by standardized testing seems like such a good idea that well-intentioned laws mandate it. However, testing also incentivizes schools to focus more on teaching students to test well, and less on teaching broadly useful skills. As a result, it can cause overall educational outcomes to become worse. Similar examples abound, in politics, economics, health, science, and many other fields.

This same counterintuitive relationship between efficiency and outcome occurs in machine learning, where it is called overfitting. Overfitting is heavily studied, somewhat theoretically understood, and has well known mitigations. This connection between the strong version of Goodhart's law in general, and overfitting in machine learning, provides a new lens for understanding bad outcomes, and new ideas for fixing them.

Overfitting and Goodhart's law

In machine learning (ML), overfitting is a pervasive phenomenon. We want to train an ML model to achieve some goal. We can't directly fit the model to the goal, so we instead train the model using some proxy which is similar to the goal.

For instance, as an occasional computer vision researcher, my goal is sometimes to prove that my new image classification model works well. I accomplish this by measuring its accuracy, after asking it to label images (is this image a cat or a dog or a frog or a truck or a ...) from a standardized test dataset of images. I'm not allowed to train my model on the test dataset though (that would be cheating), so I instead train the model on a proxy dataset, called the training dataset. I also can't directly target prediction accuracy during training1, so I instead target a proxy objective which is only related to accuracy. So rather than training my model on the goal I care about — classification accuracy on a test dataset — I instead train it using a proxy objective on a proxy dataset.

At first everything goes as we hope — the proxy improves, and since the goal is similar to the proxy, it also improves.

As we continue optimizing the proxy though, we eventually exhaust the useable similarity between proxy and goal. The proxy keeps on getting better, but the goal stops improving. In machine learning we call this overfitting, but it is also an example of Goodhart's law.

Goodhart's law states that, when a measure becomes a target, it ceases to be a good measure2. Goodhart proposed this in the context of monetary policy, but it applies far more broadly. In the context of overfitting in machine learning, it describes how the proxy objective we optimize ceases to be a good measure of the objective we care about.

The strong version of Goodhart's law: as we become too efficient, the thing we care about grows worse

If we keep on optimizing the proxy objective, even after our goal stops improving, something more worrying happens. The goal often starts getting worse, even as our proxy objective continues to improve. Not just a little bit worse either — often the goal will diverge towards infinity.

This is an extremely general phenomenon in machine learning. It mostly doesn't matter what our goal and proxy are, or what model architecture we use3. If we are very efficient at optimizing a proxy, then we make the thing it is a proxy for grow worse.

Though this pheonomenon is often discussed, it doesn't seem to be named4. Let's call it the strong version of Goodhart's law5. We can state it as:

When a measure becomes a target, if it is effectively optimized, then the thing it is designed to measure will grow worse.

Goodhart's law says that if you optimize a proxy, eventually the goal you care about will stop improving. The strong version of Goodhart's law differs in that it says that as you over-optimize, the goal you care about won't just stop improving, but will instead grow much worse than if you had done nothing at all.

Goodhart's law applies well beyond economics, where it was originally proposed. Similarly, the strong version of Goodhart's law applies well beyond machine learning. I believe it can help us understand failures in economies, governments, and social systems.

Increasing efficiency and overfitting are happening everywhere

Increasing efficiency is permeating almost every aspect of our society. If the thing that is being made more efficient is beneficial, then the increased efficiency makes the world a better place (overall, the world seems to be becoming a better place). If the thing that is being made more efficient is socially harmful, then the consequences of greater efficiency are scary or depressing (think mass surveillance, or robotic weapons). What about the most common case though — where the thing we are making more efficient is related, but not identical, to beneficial outcomes? What happens when we get better at something which is merely correlated with outcomes we care about?

In that case, we can overfit, the same as we do in machine learning. The outcomes we care about will improve for a while ... and then they will grow dramatically worse.

Below are a few, possibly facile, examples applying this analogy.

Goal: Educate children well

Proxy: Measure student and school performance on standardized tests

Strong version of Goodhart's law leads to: Schools narrowly focus on teaching students to answer questions like those on the test, at the expense of the underlying skills the test is intended to measure

Goal: Rapid progress in science

Proxy: Pay researchers a cash bonus for every publication

Strong version of Goodhart's law leads to: Publication of incorrect or incremental results, collusion between reviewers and authors, research paper mills

Goal: A well-lived life

Proxy: Maximize the reward pathway in the brain

Strong version of Goodhart's law leads to: Substance addiction, gambling addiction, days lost to doomscrolling Twitter

Goal: Healthy population

Proxy: Access to nutrient-rich food

Strong version of Goodhart's law leads to: Obesity epidemic

Goal: Leaders that act in the best interests of the population

Proxy: Leaders that have the most support in the population

Strong version of Goodhart's law leads to: Leaders whose expertise and passions center narrowly around manipulating public opinion at the expense of social outcomes

Goal: An informed, thoughtful, and involved populace

Proxy: The ease with which people can share and find ideas

Strong version of Goodhart's law leads to: Filter bubbles, conspiracy theories, parasitic memes, escalated tribalism

Goal: Distribution of labor and resources based upon the needs of society

Proxy: Capitalism

Strong version of Goodhart's law leads to: Massive wealth disparities (with incomes ranging from hundreds of dollars per year to hundreds of dollars per second), with more than a billion people living in poverty

Goal: The owners of Paperclips Unlimited, LLC, become wealthy

Proxy: Number of paperclips made by the AI-run manufacturing plant

Strong version of Goodhart's law leads to: The entire solar system, including the company owners, being converted to paperclips

As an exercise for the reader, you can think about how the strong version of Goodhart's law would apply to other efficiencies, like the ones in this list:

telepresence and virtual reality

personalized medicine

gene therapy

tailoring marketing messages to the individual consumers or voters who will find them most actionable

predicting the outcome of elections

writing code

artificial intelligence

reducing slack in supply chains

rapidly disseminating ideas

generating entertainment

identifying new products people will buy

raising livestock

trading securities

extracting fish from the ocean

constructing cars

Listing 1: Some additional diverse things we are getting more efficient at. For most of these, initial improvements were broadly beneficial, but getting too good at them could cause profound negative consequences.

How do we mitigate the problems caused by overfitting and the strong version of Goodhart's law?

If overfitting is useful as an analogy, it will be because some of the approaches that improve it in machine learning also transfer to other domains. Below, I review some of the most effective techniques from machine learning, and share some thoughts about how they might transfer.

Mitigation: Better align proxy goals with desired outcomes. In machine learning this often means carefully collecting training examples which are as similar as possible to the situation at test time. Outside of machine learning, this means changing the proxies we have control over — e.g. laws, incentives, and social norms — so that they directly encourage behavior that better aligns with our goals. This is the standard approach used to (try to) engineer social systems.

Mitigation: Add regularization penalties to the system. In machine learning, this is often performed by penalizing the squared magnitude of parameters, so that they stay small. Importantly, regularization doesn't need to directly target undesirable behavior. Almost anything that penalizes deviations of a model from typicality works well. Outside of machine learning, anything that penalizes complexity, or adds friction or extra cost to a system, can be viewed as regularization. Some example ideas:

Add a billing mechanism to SMTP, so there's a small cost for every email.

Use a progressive tax code, so that unusual success is linked to disproportionately greater cost

Charge a court fee proportional to the squared (exponentiated?) number of lawsuits initiated by an organization, so that unusual use of the court system leads to unusual expenses

Tax the number of bits of information stored about users

Mitigation: Inject noise into the system. In machine learning, this involves adding random jitter to the inputs, parameters, and internal state of a model. The unpredictability resulting from this noise makes overfitting far more difficult. Here are some ideas for how to improve outcomes by injecting noise outside of machine learning:

Stack rank all the candidates for a highly competitive school or job. Typically, offers would be made to the top-k candidates. Instead, make offers probabilistically, with probability proportional to (

[approx # top tier candidates] +

[candidate's stack rank])−1

. Benefits include: greater diversity of accepted candidates; less ridiculous resources spent by the candidates tuning their application, and by application reviewers reviewing the applications, since small changes in assessed rank only have a small effect on outcome probabilities; occasionally you will draw a longshot candidate that is more likely to fail, but also more likely to succeed in an unconventional and unusually valuable way.

Randomly time quizzes and tests in a class, rather than giving them on pre-announced dates, so that students study to understand the material more, and cram (i.e., overfit) for the test less.

Require securities exchanges to add random jitter to the times when they process trades, with a standard deviation of about a second. (An efficient market is great. Building a global financial system out of a chaotic nonstationary dynamical system with a characteristic timescale more than six orders of magnitude faster than human reaction time is just asking for trouble.)

Randomize details of the electoral system on voting day, in order to prevent candidates from overfitting to incidental details of the current electoral system (e.g. by taking unreasonable positions that appeal to a pivotal minority). For instance randomly select between ranked choice or first past the post ballots, or randomly rescale the importance of votes from different districts. (I'm not saying all of these are good ideas. Just ... ideas.)

Mitigation: Early stopping. In machine learning, it's common to monitor a third metric, besides training loss and test performance, which we call validation loss. When the validation loss starts to get worse, we stop training, even if the training loss is still improving. This is the single most effective tool we have to prevent catastrophic overfitting. Here are some ways early stopping could be applied outside of machine learning:

Sharply limit the time between a call for proposals and submission date, so that proposals better reflect pre-existing readiness, and to avoid an effect where increasing resources are poured into proposal generation, rather than being used to create something useful

Whenever stock volatility rises above a threshold, suspend all market activity

The use of antitrust law to split companies that are preventing competition in a market

Estimate the importance of a decision in $$. When the value of the time you have already spent analyzing the decision approaches that value, make a snap decision.

Freeze the information that agents are allowed to use to achieve their goals. Press blackouts in the 48 hours before an election might fall under this category.

One of the best understood causes of extreme overfitting is that the expressivity of the model being trained too closely matches the complexity of the proxy task. When the model is very weak, it can only make a little bit of progress on the task, and it doesn't exhaust the similarity between the goal and the proxy. When the model is extremely strong and expressive, it can optimize the proxy objective in isolation, without inducing extreme behavior on other objectives. When the model's expressivity roughly matches the task complexity (e.g., the number of parameters is no more than a few orders of magnitude higher or lower than the number of training examples), then it can only do well on the proxy task by doing extreme things everywhere else. See Figure 1 for a demonstration of this idea on a simple task. This cause of overfitting motivates two final, diametrically opposed, methods for mitigating the strong version of Goodhart's law.

Mitigation: Restrict capabilities / capacity. In machine learning, this is often achieved by making the model so small that it's incapable of overfitting. In the broader world, we could similarly limit the capacity of organizations or agents. Examples include:

Campaign finance limits

Set a maximum number of people that can work in companies of a given type. e.g. allow only 10 people to work in any lobbying group

Set the maximum number of parameters, or training compute, that any AI system can use.

Mitigation: Increase capabilities / capacity. In machine learning, if a model is made very big, it often has enough capacity to overfit to the training data without making performance on the test data worse. In the broader world, this would correspond to developing capabilities that are so great that there is no longer any tradeoff required between performance on the goal and the proxy. Examples include:

Obliterate all privacy, and make all the information about all people, governments, and other organizations available to everyone all the time, so that everyone can have perfect trust of everyone else. This could be achieved by legislating that every database be publicly accessible, and by putting cameras in every building. (to be clear — from my value system, this would be a dystopian scenario)

Invest in basic research in clean energy

Develop as many complex, inscrutable, and diverse market trading instruments as possible, vesting on as many timescales as possible. (In nature, more complex ecosystems are more stable. Maybe there is a parallel for markets?)

Use the largest, most compute and data intensive, AI model possible in every scenario 😮6

This last mitigation of just continuing to increase capabilities works surprisingly well in machine learning. It is also a path of least resistance. Trying to fix our institutions by blindly making them better at pursuing misaligned goals is a terrible idea though.

Parting thoughts

The strong version of Goodhart's law underlies most of my personal fears around AI (expect a future blog post about my AI fears!). If there is one thing AI will enable, it is greater efficiency, on almost all tasks, over a very short time period. We are going to need to simultaneously deal with massive numbers of diverse unwanted side effects, just as our ability to collaborate on solutions is also disrupted.

There's a lot of opportunity to research solutions to this problem. If you are a scientist looking for research ideas which are pro-social, and have the potential to create a whole new field, you should consider building formal (mathematical) bridges between results on overfitting in machine learning, and problems in economics, political science, management science, operations research, and elsewhere7. This is a goldmine waiting to be tapped. (I might actually be suggesting here that we should invent the field of psychohistory, and that overfitting phenomena will have a big role in that field.)

The more our social systems break due to the strong version of Goodhart's law, the less we will be able to take the concerted rational action required to fix them. Hopefully naming, and better understanding, the phenomenon will help push in the opposite direction.

Figure 1: Models often suffer from the strong version of Goodhart's law, and overfit catastrophically, when their complexity is well matched to the complexity of the proxy task. If a model is instead much more or much less capable than required, it will overfit less. Here, models are trained to map from a one-dimensional input x

to a one-dimensional output y

. All models are trained on the same 10 datapoints, in red. The model with 4 parameters is too weak to exactly fit the datapoints, but it smoothly approximates them. The model with 10,000 parameters is strong enough to easily fit all the datapoints, and also smoothly interpolate between them. The model with 10 parameters is exactly strong enough to fit the datapoints, but it can only contort itself to do so by behaving in extreme ways away from the training data. If asked to predict y

for a new value of x

, the 10 parameter model would perform extremely poorly. For details of this toy experiment, which uses linear random feature models, see this colab notebook.

1 Accuracy is not differentiable, which makes it impossible to target by naive gradient descent training. It is usually replaced during training by a proxy of softmax-cross-entropy loss, which is differentiable. There are blackbox training methods which can directly target accuracy, but they are inefficient and rarely used.

2 This modern phrasing is due to Marilyn Strathern. Goodhart originally phrased the observation as the more clunky any observed statistical regularity will tend to collapse once pressure is placed upon it for control purposes.

3 This glosses over a lot of variation. For instance, there is an entire subfield which studies the qualitative differences in overfitting in underparameterized, critically parameterized, and overparameterized models. Despite this variation, the core observation — that when we train on a proxy our target gets better for a while, but then grows worse — holds broadly.

4 It's not simply overfitting. Overfitting refers to the proxy becoming better than the goal, not to the goal growing worse in an absolute sense. There are other related, but not identical, concepts — for instance perverse incentives, Campbell's law, the Streisand effect, the law of unintended consequences, Jevons paradox, and the concept of negative externalities. Goodhart's curse is perhaps the closest. However, the definition of Goodhart's curse incorporates not only the phenomenon, but also a specific mechanism, and the mechanism is incorrect8. Edit 2022/11/9: Andrew Hundt suggests that similar observations that optimization isn't always desirable have been made in the social sciences, and gives specific examples of "The New Jim Code" and "Weapons of Math Destruction". Kiran Vodrahalli points out connections to robust optimization and the "price of robustness." Leo Gao points me at a recent paper which uses the descriptive term "overoptimization" for this phenomenon, which I think is good.

5 I also considered calling it the strong law of unintended consequences — it's not just that there are unexpected side effects, but that that the more effectively you accomplish your task, the more those side effects will act against your original goal.

6 Note that for suficiently strong AI, limitations on its capabilities might be determined by the laws of physics, rather than by its compute scale or training dataset size. So if you're worried about misaligned AGI, this mitigation may offer no comfort.

7 For instance, take PAC Bayes bounds from statistical learning theory, and use them to predict the optimal amount of power unions should have, in order to maximize the wealth of workers in an industry. Or, estimate the spectrum of candidate-controllable and uncontrollable variables in political contests, to predict points of political breakdown. (I'm blithely suggesting these examples as if they would be easy, and are well formed in their description. Of course, neither is true — actually doing this would require hard work and brilliance in some ratio.)

8 The definition of Goodhart's curse includes the optimizer's curse as its causal mechanism. This is where the word 'curse' comes from in its name. If an objective u

is an imperfect proxy for a goal objective v

, the optimizer's curse explains why optimizing u

finds an anomalously good u

, and makes the gap between u

and v

grow large. It doesn't explain why optimizing u

makes v

grow worse in an absolute sense. That is, the optimizer's curse provides motivation for why Goodhart's law occurs. It does not provide motivation for why the strong version of Goodhart's law occurs. (As I briefly discuss elsewhere in the post, one common causal mechanism for v

growing worse is that it's expressivity is too closely matched to the complexity of the task it is performing. This is a very active research area though, and our understanding is both incomplete and actively changing.)

Thank you to Asako Miyakawa and Katherine Lee for providing feedback on earlier drafts of this post.