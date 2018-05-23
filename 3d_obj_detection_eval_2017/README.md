# Intro

KITTI provides an official evaluation kit, which requires you do online evaluation, filling in emails and zip archives.

However, most of the time, we just wanna do local evaluation, therefore, a modified version has been used to compile. Note, some of the
offline code has been borrowed from this [repo](https://github.com/charlesq34/frustum-pointnets/blob/master/train/kitti_eval/evaluate_object_3d_offline.cpp).

# Files

We provide:

- [X] source code that can be used to compile executables

- [X] compile bash scripts that summarize the compile command

- [X] pre-compiled executables for both online and offline

# Evaluations

### Step1 Download labels

Download data object label from [KITTI](http://www.cvlibs.net/download.php?file=data_object_label_2.zip) and unzip it (then 
you pbbly can get a folder called label_2 including a bunch of txt files).

Either move all files in label_2 into the [placeholder label folder](https://github.com/KleinYuan/kitti-eval/tree/master/3d_obj_detection_eval_2017/label) 
or delete [placeholder label folder](https://github.com/KleinYuan/kitti-eval/tree/master/3d_obj_detection_eval_2017/label) 
and rename the unzipped one.

### Step2 Get prediction data

This evaluation only can be done after you have finish the predictions. Organize the predictions under 
[prediction/data](https://github.com/KleinYuan/kitti-eval/tree/master/3d_obj_detection_eval_2017/prediction/data).

Namely, you will have folder organizations as follow:

```
|---3d_object_detection_eval_2017
    |---label
        |---000000.txt
        |---000001.txt
        |.......
        |---007480.txt
    |---prediction
        |---data
        |---000000.txt
        |---000001.txt
        |.......
        |---007480.txt
```

### Step3 Run evaluation

If you organize all the data as I listed above, simply run:

```
bash evaluate.sh
```

Otherwise, you can also run:

```
./evaluate_object_3d_offline ${LABEL_FOLDER} ${PREDICT_FOLDER}
```