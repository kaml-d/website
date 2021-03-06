---
title: "What?"
type: page
date: 2018-03-04T12:00:00Z
tags: ["motivation", "use cases"]
---

&#10143; [The double divide](#the-double-divide) <br>
&#10143; [Use Cases](#use-cases) <br>
&#10143; [User story](#user-story) <br>

----

# The double divide

`KAML-D` addresses the double divide, often found in teams employing Machine Learning (ML) for their apps. Essentially, we're dealing here with four roles in three to four groups:

![ML double divide](/images/ml-dd.png)

There are two orthogonal issues to overcome (hence double divide):

1. Handoff and collaboration between _data scientists_ on the one hand and _data engineers_ and/or _developers_ on the other. `KAML-D` focuses on this challenge.
1. Handoff and collaboration between _data engineers_ and/or _developer_s on the one hand and _ops folks_ on the other. This is addressed by the devops thinking and tooling supporting you to address this issue. `KAML-D` also supports you here, albeit not our main focus.

Now that you understand what we're trying to solve, let's look into where you'd ideally use `KAML-D`.

# Use Cases

`KAML-D` is mainly useful in the area of collaboratively developing and running cloud native Machine Learning (ML) apps, for example:

- As a *data scientist*, iterate on ML-based features faster and consequently ship them faster. Share models (incl. datasets and parameters) with team colleagues in a simply and intuitive way.
- As a *data engineer* or *developer*, you can benefit from the unified way of handling both datasets and models to more smoothly transition an app to production and interact with your fellow data scientists on the team.
- In an *ops* role, you can get the insights necessary to provide guidance to run the app (incl. the ML features) optimally.

# User story

Imagine a team that works on an app that has a machine learning feature, for example a face recognition or voice recognition task. Now, the awesome data scientists develop their model, using for example R or in Python. How do they go about it? Glad you asked. They get some training data (let's say some CSV dump or maybe a ZIP with a gazillion `.png` images) and start choosing a 'good' machine learning approach, like an unsupervised or reinforcement learning approach. Every time the data scientists iterate, they adjust the training data maybe cleaning up, adding more data or whatever. Then they of course need to split out a part, maybe 30% into some test data. They're literally copying the original dataset (say `myawesomedata/`), remove/add stuff as they need and store it under a new name, maybe `myawesomedata1/` or even fancy stuff like `myawesomedata_2018-03-02_10am/`. 

This is just the learning/training phase. Once they have the model, they need to serialize it to make it available for the data engineers/developers to actual (re-implement) it in another language and/or environment such as Apache Spark or Apache Flink (in Scala) to make it production ready. No matter if they're using a proprietary format such as Tensorflow's [checkpoint files](https://www.tensorflow.org/programmers_guide/saved_model) or interchange formats such as [ONNX](https://onnx.ai/) or [CoreML](https://developer.apple.com/documentation/coreml), the model can and will change (drivers may include: new data, a better model or algorithm, etc.) and that updated model needs versioning, again, same as the dataset above.

Now, one could argue that they could use GitHub to capture the respective dataset at any given point in time but did you know GitHub has a [limit of 100MB](https://help.github.com/articles/what-is-my-disk-quota/) per file? Ah, OK, so I just put it on S3 and enable [versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) of the bucket! Sure you can do that, if you'd like to be locked into S3 ;)

What KAML-D brings to the table to remedy the situation is:

- Provide a unified approach to versioning datasets and models.
- Reduce the friction between different roles (that is, data scientists, data engineers, developers).
- Allow to focus each role on their task at hand.
- As a result, deliver new (machine learning) features faster.