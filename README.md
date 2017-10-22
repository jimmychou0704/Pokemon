# Pokemon

The motivation of this project is to see how well a RNN model is for generating images. We first let the computer 
learn about 700 images of Pokemon characters image using a RNN model with one hidden LSTM layer. Then we give the 
computer an image that is **NOT** in the previous 700 training images. We then cover about 50% of it and let the 
computer generate the missing part. The following are some figures I picked randomly. From left to right are


orginal image -> covered 50% -> generative image respectively.



<img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/790.png" width="250" hspace = 20><img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/790cover.png" width="250" hspace = 20> <img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/790pred.png" width="250" title = "haha">



<img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/783.png" width="250" hspace = 20><img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/783cover.png" width="250" hspace = 20> <img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/783pred.png" width="250" title = "haha">


<img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/778.png" width="250" hspace = 20><img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/778cover.png" width="250" hspace = 20> <img src="https://github.com/jimmychou0704/Pokemon/blob/master/git_pic/778pred.png" width="250" title = "haha">

It seems that the algorithm picks up the shape very well, although not exactly like the orginal image we can still
see it looks like an animal. 

#### Method and Data
It is exactly the same as language model. Here each image is 20x20, so we can think it is a document of 400 words.
Then we can decide the sentence length (we picked 40). We want to train the algorithm so that once 40 pixels have been 
parsed, it can predict the color of the next pixel. To achieve so, we let the first 40 pixel be training features, and the 41th pixel to be the label. The set (1,2,...,40 | 41) is a data point. The next data point is (2,3,...41 | 42) so on and so forth. For 700 images, we have 251300 data points.  

#### Possible Improvement
1. Here we only consider the relation of pixels in horrizontal direction. There are some other directions should be crucial, 
such as vertical or diagonal direction. I guess this is the idea of pixel RNN. It will be interesting to see how much pixel RNN will outperforme this simple RNN model.

2. I actually tried two layres and run many epochs on AWS EC2. But the result is actually not significantly improved. This i ssomething I don't understand at this point.
