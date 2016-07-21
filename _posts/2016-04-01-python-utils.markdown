---
layout: post
title:  "Python utils!"
date:   2016-04-01 17:36:13 -0500
categories: ic-unicamp
edit_link: 2016-04-01-python-utils.markdown
---
# Must be other post

* COPY AND PASTE VIM (clipboards)
```
"+y (copy)
"+p (paste)
```

* [Vimrc file](https://github.com/berthin/configuration-files/blob/master/.vimrc)

* [Bash-aliases](https://github.com/berthin/configuration-files/blob/master/.bash_aliases)

* [OpenCV Conda](https://github.com/menpo/conda-opencv)
* [OpenCV Contrib](https://github.com/Itseez/opencv_contrib)
* Conda package conflicts when importing modules but python.local are loaded instead

```bash
>>> print sklearn.__file__
 /Users/mac/anaconda/lib/python2.7/site-packages/sklearn/__init__.pyc
mi problema es que python busca en $HOME/.local/.... por paquetes instalados

berthin@voronoi:~$ python -c "import sklearn; print sklearn.__file__"
/home/berthin/.local/lib/python2.7/site-packages/sklearn/__init__.pyc

algunos decían que la solución era eliminar .local/lib pero otros decían que no,

la solución que encontré es : Manually edit site.py in the conda Python such that site.ENABLE_USER_SITE is False

ve a home/anaconda_directory$ locale site.py ($ find -name site.py... it must be ./lib/python2.7/site.py bash

edita esa cosa que dice

y luego ejecuta python con parámetro -c

berthin@voronoi:~$ python -s -c "import sklearn; print sklearn.__file__"
/home/berthin/anaconda/lib/python2.7/site-packages/sklearn/__init__.py

perdón, parámetro -s
```

* [How to read papers (pt)](http://posgraduando.com/fish-qtcr-5ss-leitura-artigos/)

* Compile opencv: ```g++ -ggdb `pkg-config --cflags --libs opencv` file.cpp```

* [Background detection algorithms](https://github.com/andrewssobral/bgslibrary/tree/opencv3)

## Bash

```bash
#creating directories
for i in training test validation; do mkdir  $i; done;

#mv sequences for training
mv person{11..18}_boxing_d{1..4}_uncomp.png ./training/

#mv sequences for testing
init=( 19  23  01  04)
ending=( 21  25  01  04)
for idx in "${!init[@]}"; 
do 
  for mv_action in $(eval mv person{${init[$idx]}..${ending[$idx]}}_boxing_d{1..4}_uncomp.png ./test/);
  do
    echo $mv_action;
  done;
done;

#mv sequences for validation
init=( 22  02 05)
ending=( 22  03 10)
for idx in "${!init[@]}"; 
do
  for mv_action in $(eval mv person{${init[$idx]}..${ending[$idx]}}_boxing_d{1..4}_uncomp.png ./validation/);
  do
    echo $mv_action;
  done;
done;
```

```bash
#using inkscape to get better patterns
for FILE_NAME in `ls *png`
do
BASE_NAME=`basename $FILE_NAME .png`
inkscape $BASE_NAME.png --verb=EditSelectAll --verb=SelectionTrace --verb=FileSaveAs --verb=FileQuit

PATT_IMG=`inkscape -S $BASE_NAME.svg | grep -oP image[0-9]*`

inkscape $BASE_NAME.svg --select=$PATT_IMG --verb=EditDelete --verb=FileSave --verb=FileQuit

inkscape $BASE_NAME.svg -E $BASE_NAME.eps
done
```

## Useful links

* [Cheat-sheets multiple things](https://www.cheatography.com/vjust/cheat-sheets/)
* [Ipython cheat-sheet](https://damontallen.github.io/IPython-quick-ref-sheets/)
* [IPython copy-to-clipboard](https://gist.github.com/nova77/5403446)


## Plot multiple images

```python
from pylab import plt
import numpy as np

def plt_imshowN(imgs, params = None, dim = (1,2)):                      
    fig = plt.figure()                                                          
    for i in xrange(1, np.multiply(*dim) + 1):                                  
        p = fig.add_subplot(dim[0], dim[1], i)                                  
        if params is not None and params[i-1] is not None:                      
            p.imshow(imgs[i-1], **params[i-1])                                  
        else:                                                                   
            p.imshow(imgs[i-1])                                                 
    plt.show() 

# plt_imshow([im1, im2], [None, {'cmap':'gray'}], dim=(1,2))
```

## Fourier transform

### Numpy

```python
gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)                                  
f = np.fft.fft2(gray)                                                           
fshift = np.fft.fftshift(f)                                                     
g = np.log(1+np.abs(fshift))                                                    
plt.imshow(g, vmin=np.min(g), vmax=np.max(g), cmap='gray'); plt.show() 
```

## Get circle for FFT operations

```python
def draw_circle (img_dim, radius):
    img = np.zeros(img_dim, np.uint8)
    cv2.circle(img, center=(img_dim[1]/2, img_dim[0]/2), radius=radius, color=1, thickness=cv2.FILLED)
    return img
```



