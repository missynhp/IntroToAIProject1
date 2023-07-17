# IntroToAIProject1

## Lane Line Detection 

### Project Introduction 

This project is to learn more about computer vision and artificial intelligence. I am interested in autonomy and self driving machines, so I chose to explore a lane line detection program. I feel like any good autonomy program for self-driving cars starts or incorporates lane line detection. Staying in your lane is a crucial part of driving and we can try to “teach” an AI program to do this for us. I will do this using datasets collected from Kaggle and GitHub. I will also use Python as my programming language. I will bring in libraries like numpy and pandas, as well as, plotting libraries. I will use OpenCV to analyze my image for computer vision. This was all compiled in a Jupyter Notebook. Since I am a beginner I used a pipeline that was already coded and then analyzed it using my own images. I wanted to see if I could enhance the pipeline in order to improve the accuracy in different scenarios. 

### Collecting Data 

I started the project off by searching for a good dataset. I found that Kaggle provided good open source datasets and code to start my project off. Kaggle is an open source platform available for anybody to use. In previous projects I had trouble bringing in data and images, but I was able to find a project that pulled the data in through a GitHub repository. The source code is provided in the file LaneLineDetectionOriginal.ipynb

[Kaggle](https://www.kaggle.com/code/soumya044/lane-line-detection)

[GitHub Repo  ](https://github.com/udacity/CarND-LaneLines-P1)

![image](https://github.com/missynhp/IntroToAIProject1/assets/70307254/fbcc8223-9e7b-405e-a8bc-de427115ee73)

### Training the Program

A good portion of this project was spent understanding the pipeline used for the lane line detection. The pipeline begins by grayscaling. Grayscaling removes color information from our image. 

![image](https://github.com/missynhp/IntroToAIProject1/assets/70307254/ec7353a9-7966-4475-adfc-f1e432f0b6e9)

A canny algorithm is used to detect the edges in our image. 

![image](https://github.com/missynhp/IntroToAIProject1/assets/70307254/cd10e2e3-0a05-4544-a585-03c514ee75ab)

The pipeline also implements Gaussian smoothing which is where we blur our image. This is used to get rid of non essential details and reduce noise. 
After this the region of interest masks the portion we need for lane line detection with a polygon and sets the rest of the image to black. 

![image](https://github.com/missynhp/IntroToAIProject1/assets/70307254/39c57f45-55d1-4619-83b5-eaa9d2a5a62a)

![image](https://github.com/missynhp/IntroToAIProject1/assets/70307254/4d4856f3-750a-41a2-aecc-3c292e2afd39)

Then the draw lines function draws lines on our image. The slope line is using the slope of the line to determine which line is in the image. Hough lines are used to detect straight lines. This is helpful in detecting the lines that separate lanes. The weight image function puts it all together, combining the lines that were drawn with your image. 

### Testing the Program 
To test the accuracy of this program I used images from different scenarios including Colorado roads, roads at nighttime, roads with snowy conditions, and curvy roads. I wanted to see if there were any weak areas that might possibly be improved in the pipeline. 
When testing the program on Colorado roads I found that the landscape and other surroundings did not really affect the program’s performance. However, the size and thickness of the lines did play a part. The first image I used detected the entire road to be a lane. The second image had no problems. 

<img width="326" alt="image" src="https://github.com/missynhp/IntroToAIProject1/assets/70307254/e6a5184e-60ce-4d49-8a8f-4708f0105b62">

<img width="325" alt="image" src="https://github.com/missynhp/IntroToAIProject1/assets/70307254/e3e6972c-8019-4c7b-8d44-26b4178ca585">


When using nighttime images, as long as the lines were reflective and noticeable by camera the program was fairly accurate. When you introduce a little curve the program starts to become highly inaccurate.

<img width="326" alt="image" src="https://github.com/missynhp/IntroToAIProject1/assets/70307254/dc7ae185-4ab3-4fba-aafe-6761a139c2cb">

The program does not perform well for snowy conditions. The program uses tire marks made in the snow as lanes. My last finding was that this program does not perform on any type of roads that contain any type of curve.

<img width="325" alt="image" src="https://github.com/missynhp/IntroToAIProject1/assets/70307254/e4b593ff-e87e-4018-9adb-d2297131f4f2">

<img width="325" alt="image" src="https://github.com/missynhp/IntroToAIProject1/assets/70307254/522325f0-4f2e-4da8-96f2-e7556e96c86e"> 


The program would not analyze any of the pictures that I provided with curves. The program would return errors. The only thing that seemed to happen was that the program would recognize the middle line. I tested pictures with different types of curves. 

<img width="320" alt="image" src="https://github.com/missynhp/IntroToAIProject1/assets/70307254/deb374a8-f1dc-4b40-ab48-609c40a8bc5b">

<img width="320" alt="image" src="https://github.com/missynhp/IntroToAIProject1/assets/70307254/87787e75-ff5e-4801-87ea-2615d63b4bba">


These images and their results can be found in the LLDWithMyImage.ipynb

### Future Research
I would like to see if I can’t edit the pipeline to detect snowy conditions better and provide a more accurate reading for lanes. Since cars must travel in all conditions, it would be essential to have a program that could provide accurate results in all weather conditions. 
The pipeline also needs to be modified to account for curves in the road. The pipeline using Hough to detect straight lines. If we added another algorithm that would detect curved lines we might be able to acquire the ability to detect curves in the road. 
