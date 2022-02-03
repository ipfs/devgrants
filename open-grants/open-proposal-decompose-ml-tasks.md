# Open Grant Proposal: `Decomposing the Capabilities Learned by Machine Learning Models`

**Name of Project:** Decomposing Models

**Proposer:** `craffel`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

The paradigm of *transfer learning* has increasingly become a standard way of attacking machine learning problems. In transfer learning, a pre-trained model is used as a starting point for additional training on a "downstream" task of input. The use of a pre-trained model can result in faster convergence to a better solution with less labeled data.

These benefits have spurred the widespread use and development of pre-trained models. Systems like IPFS have the potential to further the proliferation of pre-trained models, thanks to the fact that it will become significantly simpler to share and host these valuable (and typically large) artifacts.

However, despite transfer learning's successes, it only provides a crude means of transferring capabilities across models. Thinking more broadly, we might hope to decompose pre-trained models into submodels that each represent different capabilities and then recompose submodels to create new models that have the desired set of capabilities.

For example, to answer the question "how long would it take for a tennis ball to hit the ground after it was dropped from the Burj Khalifa?", the model must understand gravity, be able to perform arithmetic, and know the weight of a tennis ball and the height of the Burj Khalifa. If we have different pre-trained models that can each perform a subset of these capabilities, it would be useful to be able to extract the relevant capabilities and combine them into a new model that has the desired functionality.

We have already explored this solution space, showing that the gradient of a model's output with respect to its parameters tends to lie in a low-dimensional subspace and can be decomposed using classical methods like principal and independent component analysis. These components tend to correspond to different capabilities of the model, for example distinguishing between different subclasses of the input. We will combine this approach with our past work on [merging models](https://arxiv.org/abs/2111.09832) in order to recombine components and create new models.

A major advantage of this approach is that it does not require training any new models, which will make it dramatically cheaper than traditional gradient-based training. To perform evaluation, we will make use of the thousands of pre-trained models on the [Hugging Face model hub](https://huggingface.co/models) and show that decomposing and recombining existing models can produce new models that attain strong performance on existing NLP benchmarks.

While sharing pre-trained models is currently possible, it is typically only done for a very small subset of all of the models that could be shared. A major reason for this is the storage and transmision cost of sharing a given model Ultimately, IPFS will make it possible to store and access much larger amounts of data. This will make it significantly easier to share pre-trained models. The research in this proposal will enable a transformative way of making use of these resources that takes advantage of future possiblities enabled by IPFS.

## Value

*What are the benefits to getting this right?*

The successful culmination of this proposal will be a new paradigm for leveraging pre-trained models.
The ability to decompose models into task-specific submodels and recombine them has various advantages over traditional sequential transfer learning:
  - It will likely be more computationally efficient since it will not involve gradient-based training,
  - It will provide a means of interpreting the capabilities of a given pre-trained model,
  - It may provide a path towards creating smaller and more resource-efficient models by enabling creating models that contain the minimal set of capabilities to perform a given task.
  - It will provide a new way of leveraging pre-trained checkpoints as IPFS enables them to become more widely shared. 

*What are the risks if you don't get it right?*

Since this is a research-based proposal, it is possible that some of our proposed approaches will not succeed as we intend them to. For example, the performance of a given model on some task may degrade when it is decomposed and recombined with submodels from a different model. However, our preliminary work provides some indication that our proposed approach will be successful, and using our existing work to develop an interpretability method provides a reasonable fall-back plan.

*What are the risks that will make executing on this project difficult?*

Like all open-ended research projects, it is open-ended and its success is not guaranteed. However, we have significant background in the area as well as a great deal of experience undertaking open-ended research projects. The main failure mode that we might anticipate is that it is not possible to recombine subcomponents of a given model without sacrificing signficant performance. However, our past work on [merging pre-trained models](https://arxiv.org/abs/2111.09832) provides some preliminary evidence that this will be possible.

## Deliverables

We will produce the following deliverables:
  - A codebase implementing our proposed procedure that will be readily applicable to standard pre-trained models.
  - A website describing, in terms understandable to the typical machine learning software engineer, how to use our code and procedure for decomposing and recombining pre-trained models.
  - A publication submitted to a top-tier machine learning venue describing our approach and results.

## Development Roadmap

Since this is an open-ended research project, the exact plan and roadmap may change as we evaluate different approaches and determine what works best. Regardless of the specific approach developed, we will ultimately focus on the same final goal of enabling pre-trained models to be decomposed and recombined. The entirety of the project will be undertaken by me and one graduate research assistant.

I will serve as an advisor, helping set the direction of the project and stepping in to perform experiments, write code, and write a paper as appropriate. My graduate research assistant will perform the bulk of the work on the project.

Specifically, we will focus on the following milestones:
1. Validating our existing approach for decomposing the underlying capabilities of a pre-trained model (2 months).

    * This will include applying our technique to existing pre-trained models and analyzing the results.
    * Most of this analysis will be qualitative. We have preliminary code implementing this functionality, but we will also work to mature the codebase to make it easier to develop more advanced methods.

1. Developing methods for recombining decomposed submodels (2 months).
    * This will primarily require mapping back from the decomposition of parameter gradients to parameter values. We will make use of our past work on [merging models](https://arxiv.org/abs/2111.09832).
1. Evaluate our proposed approach on standard NLP benchmarks (2 months).
    * We will make use of pre-trained models from the [Hugging Face model hub](https://huggingface.co/models) and evaluate on standard NLP datasets from the [datasets library](https://github.com/huggingface/datasets).
    * Our codebase will aim to be a lightweight layer on top of these existing tools so that it can be easily integrated into other codebases that make use of them.
1. Write paper and prepare code for release (2 months).
    *  We will submit our work to a top-tier machine learning venue.
    * We will also release our codebase with clear documentation to make it easily applicable for practitioners.

## Total Budget Requested

We request a budget of $30,000. The entirety of this budget will go towards support of the graduate research assistant.

## Maintenance and Upgrade Plans

Our primary goal with the code produced by this project will be to serve as a demonstration of the proposed functionality.

We will base it on the popular [Hugging Face Transformers](https://huggingface.co/docs/transformers/index) library, ensuring that it will be easily adoptable.

Further, by basing our code on an established and widely-used library, we will ensure that it will be useable in the long term.

We also will publish our results in an archival venue, so that the high-level description of our algorithms is permanently available.

# Team

## Team Members and website

My lab members are listed on my website: https://colinraffel.com/

## Relevant Experience

* I have a long history of developing important pre-trained models.
* I was the lead developer of the T5 model, which remains the largest publicly-available pre-trained neural network over two years since its release.
* I led the organization of the recent ICLR 2021 Workshop on Enormous Language Models.
* I have given invited talks on the topic at workshops at NeurIPS, CVPR, ISMIR, AKBC, and many other venues. 
* Recently, I have been developing a [research agenda](https://colinraffel.com/blog/a-call-to-build-models-like-we-build-open-source-software.html) focused on making it possible to develop machine learning models in a collaborative and continual manner (much in the way that open-source software is developed).
* Preliminary work in this direction includes methods for [merging models](https://arxiv.org/abs/2111.09832) and [communication-efficient training](https://arxiv.org/abs/2111.09839).

## Team code repositories

Code for related research projects done by me and my students include:
- https://github.com/google-research/text-to-text-transfer-transformer/
- https://github.com/mmatena/model_merging
- https://github.com/varunnair18/FISH/
