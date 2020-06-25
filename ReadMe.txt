*Overview*
We have  developed a face recognition system using MATLAB to detect and identify students, using a database of known face images and videos of the cohort in the computer vision elective. This is an object detection ie classification and localization problem,which is delivered via one single function RecogniseFace.

*Folder Structure*
'Code' - Contains all scripts. Matlab current folder should point to the content of this folder.
'Models'- All classifer models < 200 MB
'Prerequisite' - Toolbox to be installed
'Report '- Report
'Screen Capture Video - 3 minute video demo-ing functionality for 2 images.
'Images - Couple of test images and smiley used for one of the creative mode options.


*Prerequisite*
1. Install Matlab ToolBox called 'MTCNN-Face-Detection'. The .mltbx file is available in the 'Prerequisite' Folder. To install, open the .mltbx file in MATLAB.Reference: https://github.com/matlab-deep-learning/mtcnn-face-detection
2. Download models >200 MB - Alexnet (cnn_tl_alexnet_MTCNN_v1.mat) and HOG_SVM(classifier_hog_svm_mtcnn_v1) from Drive path :
https://drive.google.com/drive/folders/1d_A7zjI1Xq-4flBjWKFBrLkDsaHOxpYB?usp=sharing
and place in 'Models' folder.
3. Ensure current path in MATLAB corresponds to the content of 'Code' folder for testing RecogniseFace. Test Images can be placed in the 'Images' folder.

*Details*
The RecogniseFace function will return P matrix with person id and x,y coordinates of mid-point of face, of each detected person. If a face is not detected, it will return an empty matrix with a message.

*Known limitations*
1. Returns label for the single digit ids without a preceding 0. Eg- Returns '1' instead of '01', '2' instead of '02'.This is because we have treated all ids as integers in the code.
2. Unknown person label has only been enabled for CNN.

*Inputs*
I: Image file path
featureType : 'HOG' / 'SURF' ( applicable to 'SVM'/ 'MLP')
	      'NONE'/'UNKNOWN' (applicable to 'CNN')
classifierType : 'SVM'/ 'MLP'/ 'CNN'
creativeMode : '0'/'1'/'2'/'3'/'4'
	       mode=0 no effect
	       mode=1 for sunglasses
               mode=2 for smiley face
               mode=3 for cartoon effect
               mode=4 for blur

*Example function call*
I='..\Images\Test_Grp_1.jpg'
RecogniseFace(I, 'HOG', 'SVM', '0') - Enables HOG feature extraction with SVM classifer.
RecogniseFace(I, 'HOG', 'MLP', '1') - Enables HOG feature extraction with MLP classifer.
RecogniseFace(I, 'SURF', 'SVM', '0') - Enables SURF feature extraction with SVM classifer.
RecogniseFace(I, 'SURF', 'MLP', '1') - Enables SURF feature extraction with MLP classifer.
RecogniseFace(I, 'NONE', 'CNN', '0') - Enables CNN classifer.
RecogniseFace(I, 'UNKNOWN, 'CNN', '1') - Enables CNN classifer with Unknown Person Labels
