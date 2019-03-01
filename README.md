# Character Recognition
- Handwritten Bangla Character Recognition
https://arxiv.org/pdf/1712.09872.pdf

- English Online Handwriting Recognition 
https://www.ijana.in/Special%20Issue/C29.pdf

# Text Recognition

## 0. Preprocessing
- Preprocessing and Feature Extraction for a Handwriting Recognition System 
https://www.computer.org/csdl/proceedings/icdar/1993/4960/00/00395706.pdf


## 1. Classic computer vision techniques

![ocr](https://raw.githubusercontent.com/ritchieng/machine-learning-stanford/master/w11_application_example_ocr/photoocr.png)





## 2. Specialized deep learning approaches
### 1) EAST( Efficient accurate scene text detector)

### 2) RCNN(Convolutional-recurrent neural network)
![RCNN](https://cdn-images-1.medium.com/max/800/0*nGWtig3Cd0Jma2nX)

### 3) STN-net/SEE(Semi-Supervised End-to-End Scene Text Recognition)
![STN](https://cdn-images-1.medium.com/max/800/1*XAUtH9C1iPLa9clk9RA-8Q.png)

### ex)
- Build a Handwritten Text Recognition System using TensorFlow (CNN + RNN + CTC layer)
https://towardsdatascience.com/build-a-handwritten-text-recognition-system-using-tensorflow-2326a3487cd5
https://github.com/tesseract-ocr/docs



## 3. Standard deep learning approach
SSD, YOLO model, Mask RCNN

# application
Google Cloud Vision API
![API](https://cdn-images-1.medium.com/max/800/1*2aEAFgnCSpPaPf4wu0rP1g.png)
https://towardsdatascience.com/secret-of-google-web-based-ocr-service-fe30eecedd01

=> 최근 모델
https://github.com/tesseract-ocr/docs/blob/master/das_tutorial2016/6ModernizationEfforts.pdf

### link


- OCR 기본 및 전체 설명
https://towardsdatascience.com/a-gentle-introduction-to-ocr-ee1469a201aa

- 최신 OCR 모델 with keras
https://hackernoon.com/latest-deep-learning-ocr-with-keras-and-supervisely-in-15-minutes-34aecd630ed8
![LSTM](https://cdn-images-1.medium.com/max/2000/1*sdb9_e5LVSJnxivblcFxEg.png)

- OCR 관련논문
https://das2018.cvl.tuwien.ac.at/media/filer_public/85/fd/85fd4698-040f-45f4-8fcc-56d66533b82d/das2018_short_papers.pdf

Character Recognition
https://pdfs.semanticscholar.org/8fa4/5b60e78b3d7cc26271dfa79baea66e7d13ce.pdf





-----------------------------------------------------------------
##Install baidu warpctc

    cd ~/
    git clone https://github.com/baidu-research/warp-ctc
    cd warp-ctc
    mkdir build
    cd build
    cmake ..
    make
    sudo make install

--> 결과물 ~/warp-ctc/build/libwarpctc.so

--------------------------------------------------------------------
##Install mxnet and Binding warpctc

    git clone --recursive https://github.com/Xilinx/mxnet

    comment out following lines in make/config.mk
    WARPCTC_PATH = $(HOME)/warp-ctc
    MXNET_PLUGINS += plugin/warpctc/warpctc.mk

    make clean && make -j4

~/mxnet/python/ 에서

you can change in setup.py :

      packages=[
          'mxnet', 'mxnet.module', 'mxnet._ctypes', 'mxnet.rnn',
          'mxnet._cy2', 'mxnet._cy3', 'mxnet.notebook', 'mxnet.contrib',
          ],
by

      packages=[
          'mxnet', 'mxnet.module', 'mxnet._ctypes', 'mxnet.rnn',
          'mxnet._cy2', 'mxnet._cy3', 'mxnet.notebook', 'mxnet.contrib',
          'mxnet.gluon', 'mxnet.gluon.nn', 'mxnet.gluon.rnn'
          ],

and

    python setup.py clean
    python setup.py install


finally

    export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
