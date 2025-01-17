# O'Reilly Book Coming Early 2021

## Data Science on AWS

YouTube Videos, Meetups, Book, and Code:  **https://datascienceonaws.com**

[![Data Science on AWS](img/data-science-on-aws-book.png)](https://datascienceonaws.com)


# Workshop Description

In this workshop, we build a natural language processing (NLP) model to classify sample Twitter comments and customer-support emails using the state-of-the-art [BERT](https://arxiv.org/abs/1810.04805) model for language representation.

To build our BERT-based NLP model, we use the [Amazon Customer Reviews Dataset](https://s3.amazonaws.com/amazon-reviews-pds/readme.html) which contains 150+ million customer reviews from Amazon.com for the 20 year period between 1995 and 2015.  In particular, we train a classifier to predict the `star_rating` (1 is bad, 5 is good) from the `review_body` (free-form review text).


# Workshop Cost
This workshop is FREE, but would otherwise cost <25 USD.

![Workshop Cost](img/billing.png)


# Workshop Agenda

![Workshop Agenda](img/outline.png)


# Workshop Contributors

![Workshop Contributors](img/primary-contributors.png)


# Workshop Instructions

## 1. Create `TeamRole` IAM Role

![IAM](img/alt_iam_1.png)

![Roles](img/alt_roles_2.png)

![Create Role](img/alt_create_role_3.png)

![Select Service](img/alt_select_service_4.png)

![Select Policy](img/alt_select_policy_5.png)

![Add Tags](img/alt_add_tags_6.png)

![Review Name](img/alt_review_name_7.png)


## 2. Launch an Amazon SageMaker Notebook Instance

Open the [AWS Management Console](https://console.aws.amazon.com/console/home)

![Back to SageMaker](img/alt_back_to_sagemaker_8.png)

In the AWS Console search bar, type `SageMaker` and select `Amazon SageMaker` to open the service console.

![Notebook Instances](img/alt_notebook_instances_9.png)

![Create Notebook Part 1](img/alt_create_notebook_10.png)

In the Notebook instance name text box, enter `workshop`.

Choose `ml.t3.medium` (or alternatively `ml.t2.medium`). We'll only be using this instance to launch jobs. The training job themselves will run either on a SageMaker managed cluster or an Amazon EKS cluster.

Volume size `250` - this is needed to explore datasets, build docker containers, and more.  During training data is copied directly from Amazon S3 to the training cluster when using SageMaker.  When using Amazon EKS, we'll setup a distributed file system that worker nodes will use to get access to training data.

![Fill notebook instance](img/alt-notebook-setup01.png)

In the IAM role box, select the default `TeamRole`.

![Fill notebook instance](img/notebook-setup02.png)

You must select the default `VPC`, `Subnet`, and `Security group` as shown in the screenshow.  Your values will likely be different.  This is OK.

Keep the default settings for the other options not highlighted in red, and click `Create notebook instance`.  On the `Notebook instances` section you should see the status change from `Pending` -> `InService`

![Fill notebook instance](img/alt-notebook-setup03.png)

While the notebook spins up, continue to work on the next section.  We'll come back to the notebook when it's ready.


## 3. Update IAM Role Policy

Click on the `notebook` instance to see the instance details.

![Notebook Instance Details](img/alt_click_notebook_instance.png)

Click on the IAM role link and navigate to the IAM Management Console.

![IAM Role](img/alt_update_iam.png)

Click `Attach Policies`.

![IAM Policy](img/alt_view_policies.png)
              
Select `IAMFullAccess` and click on `Attach Policy`.

_Note:  Reminder that you should allow access only to the resources that you need._ 

![Attach Admin Policy](img/alt_attach_policies.png)

Confirm the Policies

![Confirm Policies](img/alt_confirm_policies.png)



## 4. Start the Jupyter notebook

_Note:  Proceed when the status of the notebook instance changes from `Pending` to `InService`._

![Back to SageMaker Notebooks](img/alt_back_to_sagemaker_8.png)

![Start Jupyter](img/alt_start_jupyter.png)


## 5. Launch a new Terminal within the Jupyter notebook

Click `File` > `New` > [...scroll down...] `Terminal` to launch a terminal in your Jupyter instance.

![](img/launch_jupyter_terminal.png)


## 6. Clone this GitHub Repo in the Terminal

```
cd ~/SageMaker && git clone https://github.com/data-science-on-aws/workshop
```

![](img/clone-workshop-repo.png)

Within the Jupyter terminal, run the following:

```
cd ~/SageMaker && git clone https://github.com/data-science-on-aws/workshop
```

## 7. Navigate Back to Notebook View

![](img/back-to-jupyter-notebook.png)


## 8. Start the Workshop!
Navigate to `01_setup/` in your Jupyter notebook and start the workshop!

_You may need to refresh your browser if you don't see the new `workshop/` directory._

![Start Workshop](img/start_workshop.png)
