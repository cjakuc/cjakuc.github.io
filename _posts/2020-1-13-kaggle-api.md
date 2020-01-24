---
layout: post
title: Using the Kaggle API to Import Datasets into Google Colaboratory
subtitle: This code works as of January 13th, 2020.
---
The first step is to create a Kaggle account and generate an API key. Once logged in, click on your profile picture in the top right and select **My Account**. Scroll down and click **Create New API Token**. This will prompt the download of a JSON file named *kaggle.json* containing your Kaggle username and personal API token.

![](/img/blog1_1.png)

In your Google Colab notebook, make sure that the Kaggle package is installed using the **pip command.

`!pip install kaggle`

Next, create a directory called *.kaggle* where you can store the JSON file that contains your API token details.

`!mkdir .kaggle`

Now you can ensure that you've created this directory.

`!ls -a`

If done correctly, the output will contain *.kaggle.*

Open up the *kaggle.json* file that you previously downloaded and it should look like this:

{"username":"YOUR USERNAME","key":"YOUR API KEY"}

Put your information into this next chunk of code and run it to save it in the correct location.

```
import json
token = {"username":"YOUR USERNAME","key":"YOUR API KEY"}
with open('/root/.kaggle/kaggle.json', 'w') as file:
    json.dump(token, file)
```

Kaggle's API [documentation](https://github.com/Kaggle/kaggle-api) recommends running the next line of code to prevent other users of your computer from accessing your credentials.

`!chmod 600 /root/.kaggle/kaggle.json`

Now you can go to Kaggle and find your desired dataset. For this tutorial I will be using data from [this](https://www.kaggle.com/c/ashrae-energy-prediction/data) page, the Ashrae Energy predictor competition. In the section labeled Data you can find a link to copy the download command to your clipboard.

![](/img/blog1_2.png)

Paste the copied command in a new code chunk and don't forget the exclamation point!

`!kaggle competitions download -c ashrae-energy-prediction`

The data you have downloaded from Kaggle should now be in your Google Colab environment. To check this, click on the arrow in the upper left of the screen (hovering over the arrow prompts you with "Open the left pane"):

![](/img/blog1_3.png)

This should open a a panel with the files you have uploaded. For the Ashrae Energy data it will look something like this (I've already unzipped the zipped files, I will show you how to do this next):

![](/img/blog1_4.png)

At this point you can read in your data using pandas, after unzipping the files that are zipped.

```
import pandas as pd
building = pd.read_csv('building_metadata.csv')
!unzip test.csv.zip
test = pd.read_csv('test.csv')
!unzip train.csv.zip
train = pd.read_csv('train.csv')
!unzip weather_test.csv.zip
weather_test = pd.read_csv('weather_test.csv')
!unzip weather_train.csv.zip
weather_train = pd.read_csv('weather_train.csv')
```

Now you can do whatever you like with your data! Please let me know if you find any errors or other potential solutions. I hope this has been a helpful tutorial for your data science journey!
