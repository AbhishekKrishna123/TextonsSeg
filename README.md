# TextonsSeg
Repo for PyPi package
# Textons - Texture Based Image Segmentation
Textons using LM filters

The code here is an implementation of textons using LM filters.

The image is mapped into a 48 dimensions vector space using the features obtained from the LM filters along with the features obtained it also takes into account the RGB values of the pixels

Three more features are added to the end of each vector. These features are row, col and centroids allocated for each pixel, the resulting vector is of the size (1 X 54)

K-Means using Eculidean distance is used to segment image.

inputs:
1. image ==> numpy array
2. number of cluster centers ==> integer
3. number of iterations ==> integers
4. type of colors assignment in the final image ==> integer 0 for 'RANDOM' or 1 for'DEFINED'
            
output:
* numpy array of image after k means wiht LM filters
            
Assignment type 'RANDOM' is suited more for higher number of clusters,
assignment type 'DEFINED' is better suited when number of clusters is less than 15,
however the assignemnt types do not impact the performance of the code in any significant way


To run the script 

```
from texton_color_utils import Textons

im = cv2.imread('path_to_image')
textons = Textons(im, number_of_clusters, number_of_iterations, assignment_type)
tex = textons.textons()
cv2.imshow("window name", tex)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

Example 
```
from texton_color_utils import Textons

im = cv2.imread('image.jpg')
textons = Textons(im, 5, 25, 1)
tex = textons.textons()
cv2.imshow("check", tex)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


*  Advisable to keep number of iterations high (recommended >= 100) for reproducibility of result

### Improved Reproducibility of Result
* Added feature to make the results reproducible 



 Result with 10 iterations and K value as 3
 
 
![original image](https://github.com/BATspock/Textons-colors/blob/master/5.jpg)      ![segmented image](https://github.com/BATspock/Textons-colors/blob/master/check.png)


### To-Do
- [ ] Add feature to stop k means on the basis of accuracy
- [ ] Add minkowski and mahalanobis distance as distance measure
