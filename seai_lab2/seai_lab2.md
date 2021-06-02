
## SEAI 2021 - Python - Lab 2
# Spatial data and W matrices

Vincenzo Nardelli - vincnardelli@gmail.com - https://github.com/vincnardelli



Before to start... install Python Libraries!


```python
! pip install pysal
! pip install cartoframes 
! pip install --user urllib3==1.22
```

    Collecting pysal
      Downloading https://files.pythonhosted.org/packages/c0/3e/179620647a54eef9ef8173ee82a42b0e33b1e80bbce21998ba8ffc62a0f7/pysal-2.4.0.tar.gz
    Collecting libpysal>=4.4.0
    [?25l  Downloading https://files.pythonhosted.org/packages/cc/e9/36be6aeea8b6d6ac797c656e1f80bdaddc075d049433495680432d9aedd9/libpysal-4.4.0-py3-none-any.whl (2.4MB)
    [K     |████████████████████████████████| 2.4MB 11.2MB/s 
    [?25hCollecting access>=1.1.3
      Downloading https://files.pythonhosted.org/packages/41/50/d7fb5466976af95e4c3481f8408f29744e9411e46a3f9d610a95e741f57b/access-1.1.3-py3-none-any.whl
    Collecting esda>=2.3.6
    [?25l  Downloading https://files.pythonhosted.org/packages/20/02/7c36f3c7c22f048f50ada6402ff3fbe51e0c5365f7d0227196b84d43c82b/esda-2.3.6-py3-none-any.whl (102kB)
    [K     |████████████████████████████████| 112kB 39.5MB/s 
    [?25hCollecting giddy>=2.3.3
    [?25l  Downloading https://files.pythonhosted.org/packages/5c/71/f7fc2b41e36b2a06bac30937435d2dedd125f74f3157213ec121ff52d961/giddy-2.3.3-py3-none-any.whl (60kB)
    [K     |████████████████████████████████| 61kB 6.7MB/s 
    [?25hCollecting inequality>=1.0.0
      Downloading https://files.pythonhosted.org/packages/74/0f/9ed2d097f29160d0c873f33ffc0b9806c1083e3611acb2143eb66adcf580/inequality-1.0.0.tar.gz
    Collecting pointpats>=2.2.0
    [?25l  Downloading https://files.pythonhosted.org/packages/5f/2b/a3e99c42b37c3e848eb8e55f2ee2b2d281ae0d49df261f13eaaeba7171a5/pointpats-2.2.0.tar.gz (55kB)
    [K     |████████████████████████████████| 61kB 7.2MB/s 
    [?25hCollecting segregation>=1.5.0
    [?25l  Downloading https://files.pythonhosted.org/packages/21/82/db8d8f2c25d52e774dcdc65861853f87566c7512204764d1b34acf2d7e50/segregation-1.5.0-py3-none-any.whl (82kB)
    [K     |████████████████████████████████| 92kB 9.8MB/s 
    [?25hCollecting spaghetti>=1.5.6
    [?25l  Downloading https://files.pythonhosted.org/packages/55/c6/eda10343af40be748218b3e4a8502e5fbf4e882eef8cba8025ada7cdd313/spaghetti-1.5.6-py3-none-any.whl (43kB)
    [K     |████████████████████████████████| 51kB 6.3MB/s 
    [?25hCollecting mgwr>=2.1.2
    [?25l  Downloading https://files.pythonhosted.org/packages/8e/14/e18342b62655ec7f37624ff936d6f273f82b51913cd558110fd4d670794e/mgwr-2.1.2.tar.gz (41kB)
    [K     |████████████████████████████████| 51kB 5.8MB/s 
    [?25hCollecting spglm>=1.0.8
      Downloading https://files.pythonhosted.org/packages/07/8f/03f07807967595d2632dbe0f7c442511a5ff422103b49c76557f9eed40c5/spglm-1.0.8.tar.gz
    Collecting spint>=1.0.7
      Downloading https://files.pythonhosted.org/packages/7e/c5/e4862ab3f745a1886135b07e498e77504c14e468d0a6b89f7270f5def979/spint-1.0.7.tar.gz
    Collecting spreg>=1.2.2
    [?25l  Downloading https://files.pythonhosted.org/packages/40/2d/b6559677b66b2f228fdf02fdb5e7da3466057f9e2c696bea7704138ae346/spreg-1.2.2-py3-none-any.whl (209kB)
    [K     |████████████████████████████████| 215kB 35.8MB/s 
    [?25hCollecting spvcm>=0.3.0
    [?25l  Downloading https://files.pythonhosted.org/packages/b4/c9/43fb98bc60728b76fceee175119a1ff7e5033ed9012d07570e34a2a19a8f/spvcm-0.3.0.tar.gz (5.7MB)
    [K     |████████████████████████████████| 5.7MB 15.2MB/s 
    [?25hCollecting tobler>=0.6.0
      Downloading https://files.pythonhosted.org/packages/5c/88/93acf0ad7c724565975924649928ea9db00e8d94279eb40c7819708b6105/tobler-0.7.0-py3-none-any.whl
    Collecting mapclassify>=2.4.2
      Downloading https://files.pythonhosted.org/packages/22/8e/d968c0945d41bb02de0efaa92e31e43a817dc52d30e82b4dfdda407a1903/mapclassify-2.4.2-py3-none-any.whl
    Collecting splot>=1.1.3
      Downloading https://files.pythonhosted.org/packages/83/1c/afb3e3eeeda4eef065f0b3249ca74cbcc44af3bc59ddb5a21b5445753955/splot-1.1.3.tar.gz
    Collecting spopt>=0.1.1
    [?25l  Downloading https://files.pythonhosted.org/packages/a9/df/c8ce65a07f7ab1e69b721533b950dd9854f2f7e6a472eca60c13f5770e24/spopt-0.1.1-py3-none-any.whl (54kB)
    [K     |████████████████████████████████| 61kB 6.6MB/s 
    [?25hCollecting urllib3>=1.26
    [?25l  Downloading https://files.pythonhosted.org/packages/0c/cd/1e2ec680ec7b09846dc6e605f5a7709dfb9d7128e51a026e7154e18a234e/urllib3-1.26.5-py2.py3-none-any.whl (138kB)
    [K     |████████████████████████████████| 143kB 44.6MB/s 
    [?25hCollecting python-dateutil<=2.8.0
    [?25l  Downloading https://files.pythonhosted.org/packages/41/17/c62faccbfbd163c7f57f3844689e3a78bae1f403648a6afb1d0866d87fbb/python_dateutil-2.8.0-py2.py3-none-any.whl (226kB)
    [K     |████████████████████████████████| 235kB 44.4MB/s 
    [?25hRequirement already satisfied: pytest in /usr/local/lib/python3.7/dist-packages (from pysal) (3.6.4)
    Collecting pytest-cov
      Downloading https://files.pythonhosted.org/packages/ba/84/576b071aef9ac9301e5c0ff35d117e12db50b87da6f12e745e9c5f745cc2/pytest_cov-2.12.1-py2.py3-none-any.whl
    Requirement already satisfied: coverage in /usr/local/lib/python3.7/dist-packages (from pysal) (3.7.1)
    Requirement already satisfied: scipy>=0.11 in /usr/local/lib/python3.7/dist-packages (from libpysal>=4.4.0->pysal) (1.4.1)
    Requirement already satisfied: requests in /usr/local/lib/python3.7/dist-packages (from libpysal>=4.4.0->pysal) (2.23.0)
    Requirement already satisfied: numpy>=1.3 in /usr/local/lib/python3.7/dist-packages (from libpysal>=4.4.0->pysal) (1.19.5)
    Requirement already satisfied: beautifulsoup4 in /usr/local/lib/python3.7/dist-packages (from libpysal>=4.4.0->pysal) (4.6.3)
    Requirement already satisfied: pandas in /usr/local/lib/python3.7/dist-packages (from libpysal>=4.4.0->pysal) (1.1.5)
    Requirement already satisfied: jinja2 in /usr/local/lib/python3.7/dist-packages (from libpysal>=4.4.0->pysal) (2.11.3)
    Requirement already satisfied: scikit-learn in /usr/local/lib/python3.7/dist-packages (from esda>=2.3.6->pysal) (0.22.2.post1)
    Collecting quantecon>=0.4.7
    [?25l  Downloading https://files.pythonhosted.org/packages/7e/6b/e78ec352947208c6172e50dcb086f95f7b63eb5204f26f46b676ed5bb31c/quantecon-0.5.0-py3-none-any.whl (229kB)
    [K     |████████████████████████████████| 235kB 47.8MB/s 
    [?25hRequirement already satisfied: matplotlib in /usr/local/lib/python3.7/dist-packages (from pointpats>=2.2.0->pysal) (3.2.2)
    Collecting opencv-contrib-python>=4.2.0
    [?25l  Downloading https://files.pythonhosted.org/packages/43/77/347867aff4a9a5b56ea587a50762fb0ba40b27bb4e8f8f27c25ba57ed807/opencv_contrib_python-4.5.2.52-cp37-cp37m-manylinux2014_x86_64.whl (57.4MB)
    [K     |████████████████████████████████| 57.4MB 66kB/s 
    [?25hRequirement already satisfied: seaborn in /usr/local/lib/python3.7/dist-packages (from segregation>=1.5.0->pysal) (0.11.1)
    Collecting geopandas
    [?25l  Downloading https://files.pythonhosted.org/packages/d7/bf/e9cefb69d39155d122b6ddca53893b61535fa6ffdad70bf5ef708977f53f/geopandas-0.9.0-py2.py3-none-any.whl (994kB)
    [K     |████████████████████████████████| 1.0MB 35.2MB/s 
    [?25hRequirement already satisfied: tqdm in /usr/local/lib/python3.7/dist-packages (from segregation>=1.5.0->pysal) (4.41.1)
    Collecting rtree
    [?25l  Downloading https://files.pythonhosted.org/packages/51/05/5a67111cee91d2165a2bcb855f442186e3d76ddef834596cc84d4875c401/Rtree-0.9.7-cp37-cp37m-manylinux2010_x86_64.whl (994kB)
    [K     |████████████████████████████████| 1.0MB 30.8MB/s 
    [?25hRequirement already satisfied: statsmodels in /usr/local/lib/python3.7/dist-packages (from tobler>=0.6.0->pysal) (0.10.2)
    Collecting rasterio
    [?25l  Downloading https://files.pythonhosted.org/packages/0e/78/c69f7457b7dad6163abde2772abd4c8c0c6498d2ab9fd3f3b0eb73b40951/rasterio-1.2.4-cp37-cp37m-manylinux1_x86_64.whl (19.3MB)
    [K     |████████████████████████████████| 19.3MB 245kB/s 
    [?25hCollecting pygeos
    [?25l  Downloading https://files.pythonhosted.org/packages/2a/c0/c3c0ebaa718166af6ff03a4e575d4d1ff4ffbd3ccb658be4285fbeaf3c89/pygeos-0.10-cp37-cp37m-manylinux_2_5_x86_64.manylinux1_x86_64.whl (2.0MB)
    [K     |████████████████████████████████| 2.0MB 25.3MB/s 
    [?25hCollecting rasterstats
      Downloading https://files.pythonhosted.org/packages/9f/52/055b2b736e4aa1126c4619a561b44c3bc30fbe48025e6f3275b92928a0a0/rasterstats-0.15.0-py3-none-any.whl
    Requirement already satisfied: joblib in /usr/local/lib/python3.7/dist-packages (from tobler>=0.6.0->pysal) (1.0.1)
    Requirement already satisfied: networkx in /usr/local/lib/python3.7/dist-packages (from mapclassify>=2.4.2->pysal) (2.5.1)
    Requirement already satisfied: descartes in /usr/local/lib/python3.7/dist-packages (from splot>=1.1.3->pysal) (1.1.0)
    Collecting pulp
    [?25l  Downloading https://files.pythonhosted.org/packages/14/c4/0eec14a0123209c261de6ff154ef3be5cad3fd557c084f468356662e0585/PuLP-2.4-py3-none-any.whl (40.6MB)
    [K     |████████████████████████████████| 40.6MB 98kB/s 
    [?25hRequirement already satisfied: six>=1.5 in /usr/local/lib/python3.7/dist-packages (from python-dateutil<=2.8.0->pysal) (1.15.0)
    Requirement already satisfied: setuptools in /usr/local/lib/python3.7/dist-packages (from pytest->pysal) (56.1.0)
    Requirement already satisfied: atomicwrites>=1.0 in /usr/local/lib/python3.7/dist-packages (from pytest->pysal) (1.4.0)
    Requirement already satisfied: pluggy<0.8,>=0.5 in /usr/local/lib/python3.7/dist-packages (from pytest->pysal) (0.7.1)
    Requirement already satisfied: py>=1.5.0 in /usr/local/lib/python3.7/dist-packages (from pytest->pysal) (1.10.0)
    Requirement already satisfied: attrs>=17.4.0 in /usr/local/lib/python3.7/dist-packages (from pytest->pysal) (21.2.0)
    Requirement already satisfied: more-itertools>=4.0.0 in /usr/local/lib/python3.7/dist-packages (from pytest->pysal) (8.7.0)
    Requirement already satisfied: toml in /usr/local/lib/python3.7/dist-packages (from pytest-cov->pysal) (0.10.2)
    Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.7/dist-packages (from requests->libpysal>=4.4.0->pysal) (2020.12.5)
    Requirement already satisfied: idna<3,>=2.5 in /usr/local/lib/python3.7/dist-packages (from requests->libpysal>=4.4.0->pysal) (2.10)
    Requirement already satisfied: chardet<4,>=3.0.2 in /usr/local/lib/python3.7/dist-packages (from requests->libpysal>=4.4.0->pysal) (3.0.4)
    Requirement already satisfied: pytz>=2017.2 in /usr/local/lib/python3.7/dist-packages (from pandas->libpysal>=4.4.0->pysal) (2018.9)
    Requirement already satisfied: MarkupSafe>=0.23 in /usr/local/lib/python3.7/dist-packages (from jinja2->libpysal>=4.4.0->pysal) (2.0.1)
    Requirement already satisfied: sympy in /usr/local/lib/python3.7/dist-packages (from quantecon>=0.4.7->giddy>=2.3.3->pysal) (1.7.1)
    Requirement already satisfied: numba>=0.38 in /usr/local/lib/python3.7/dist-packages (from quantecon>=0.4.7->giddy>=2.3.3->pysal) (0.51.2)
    Requirement already satisfied: pyparsing!=2.0.4,!=2.1.2,!=2.1.6,>=2.0.1 in /usr/local/lib/python3.7/dist-packages (from matplotlib->pointpats>=2.2.0->pysal) (2.4.7)
    Requirement already satisfied: kiwisolver>=1.0.1 in /usr/local/lib/python3.7/dist-packages (from matplotlib->pointpats>=2.2.0->pysal) (1.3.1)
    Requirement already satisfied: cycler>=0.10 in /usr/local/lib/python3.7/dist-packages (from matplotlib->pointpats>=2.2.0->pysal) (0.10.0)
    Collecting fiona>=1.8
    [?25l  Downloading https://files.pythonhosted.org/packages/9c/fc/9807326c37a6bfb2393ae3e1cca147aa74844562c4d5daa782d6e97ad2bc/Fiona-1.8.20-cp37-cp37m-manylinux1_x86_64.whl (15.4MB)
    [K     |████████████████████████████████| 15.4MB 283kB/s 
    [?25hRequirement already satisfied: shapely>=1.6 in /usr/local/lib/python3.7/dist-packages (from geopandas->segregation>=1.5.0->pysal) (1.7.1)
    Collecting pyproj>=2.2.0
    [?25l  Downloading https://files.pythonhosted.org/packages/11/1d/1c54c672c2faf08d28fe78e15d664c048f786225bef95ad87b6c435cf69e/pyproj-3.1.0-cp37-cp37m-manylinux2010_x86_64.whl (6.6MB)
    [K     |████████████████████████████████| 6.6MB 23.6MB/s 
    [?25hRequirement already satisfied: patsy>=0.4.0 in /usr/local/lib/python3.7/dist-packages (from statsmodels->tobler>=0.6.0->pysal) (0.5.1)
    Collecting click-plugins
      Downloading https://files.pythonhosted.org/packages/e9/da/824b92d9942f4e472702488857914bdd50f73021efea15b4cad9aca8ecef/click_plugins-1.1.1-py2.py3-none-any.whl
    Collecting snuggs>=1.4.1
      Downloading https://files.pythonhosted.org/packages/cc/0e/d27d6e806d6c0d1a2cfdc5d1f088e42339a0a54a09c3343f7f81ec8947ea/snuggs-1.4.7-py3-none-any.whl
    Requirement already satisfied: click>=4.0 in /usr/local/lib/python3.7/dist-packages (from rasterio->tobler>=0.6.0->pysal) (7.1.2)
    Collecting cligj>=0.5
      Downloading https://files.pythonhosted.org/packages/73/86/43fa9f15c5b9fb6e82620428827cd3c284aa933431405d1bcf5231ae3d3e/cligj-0.7.2-py3-none-any.whl
    Collecting affine
      Downloading https://files.pythonhosted.org/packages/ac/a6/1a39a1ede71210e3ddaf623982b06ecfc5c5c03741ae659073159184cd3e/affine-2.3.0-py2.py3-none-any.whl
    Collecting simplejson
    [?25l  Downloading https://files.pythonhosted.org/packages/a8/04/377418ac1e530ce2a196b54c6552c018fdf1fe776718053efb1f216bffcd/simplejson-3.17.2-cp37-cp37m-manylinux2010_x86_64.whl (128kB)
    [K     |████████████████████████████████| 133kB 50.8MB/s 
    [?25hRequirement already satisfied: decorator<5,>=4.3 in /usr/local/lib/python3.7/dist-packages (from networkx->mapclassify>=2.4.2->pysal) (4.4.2)
    Collecting amply>=0.1.2
      Downloading https://files.pythonhosted.org/packages/f3/c5/dfa09dd2595a2ab2ab4e6fa7bebef9565812722e1980d04b0edce5032066/amply-0.1.4-py3-none-any.whl
    Requirement already satisfied: mpmath>=0.19 in /usr/local/lib/python3.7/dist-packages (from sympy->quantecon>=0.4.7->giddy>=2.3.3->pysal) (1.2.1)
    Requirement already satisfied: llvmlite<0.35,>=0.34.0.dev0 in /usr/local/lib/python3.7/dist-packages (from numba>=0.38->quantecon>=0.4.7->giddy>=2.3.3->pysal) (0.34.0)
    Collecting munch
      Downloading https://files.pythonhosted.org/packages/cc/ab/85d8da5c9a45e072301beb37ad7f833cd344e04c817d97e0cc75681d248f/munch-2.5.0-py2.py3-none-any.whl
    Requirement already satisfied: docutils>=0.3 in /usr/local/lib/python3.7/dist-packages (from amply>=0.1.2->pulp->spopt>=0.1.1->pysal) (0.17.1)
    Building wheels for collected packages: pysal, inequality, pointpats, mgwr, spglm, spint, spvcm, splot
      Building wheel for pysal (setup.py) ... [?25l[?25hdone
      Created wheel for pysal: filename=pysal-2.4.0-cp37-none-any.whl size=18960 sha256=18433de2e3dda444414e1e2c761aa3d3608a5916fc480052d2e9c69b623ffd5e
      Stored in directory: /root/.cache/pip/wheels/48/c0/2f/ec47118138a00fa2f359e4ad28fe87b393c0c03e2041986ae2
      Building wheel for inequality (setup.py) ... [?25l[?25hdone
      Created wheel for inequality: filename=inequality-1.0.0-cp37-none-any.whl size=11801 sha256=9a74350e046a5dbfd60135667a7f3fff3e7846484561c60980ee6838b01a8ce8
      Stored in directory: /root/.cache/pip/wheels/0e/cc/44/666696f89f7c7b13cc477bd9c1a9aef180be238550419007f2
      Building wheel for pointpats (setup.py) ... [?25l[?25hdone
      Created wheel for pointpats: filename=pointpats-2.2.0-cp37-none-any.whl size=60818 sha256=b290e5cb4083748ee99a8ae64ef7cabbf92aeab1c323326df1fe3b16384ba7f2
      Stored in directory: /root/.cache/pip/wheels/f9/28/f2/65c0993e68e25cef954ecd20abff91c6b11f0419f31b60e2ff
      Building wheel for mgwr (setup.py) ... [?25l[?25hdone
      Created wheel for mgwr: filename=mgwr-2.1.2-cp37-none-any.whl size=46374 sha256=dff46014724529ff0acf437425a37e0d2b46a473c28704ce0309f99d4d58919e
      Stored in directory: /root/.cache/pip/wheels/cf/11/e3/68692f1c637b23a8e2c6e200f6183c3502718b5f7de6dc630d
      Building wheel for spglm (setup.py) ... [?25l[?25hdone
      Created wheel for spglm: filename=spglm-1.0.8-cp37-none-any.whl size=38807 sha256=84dcf591ba90dde5fb8252175b8fa749ce659d637044bd405c5c49012190b90a
      Stored in directory: /root/.cache/pip/wheels/cd/1e/e3/c68bde79087fdc97cf65ec86e6d1d7ed2171e1baa1b0482363
      Building wheel for spint (setup.py) ... [?25l[?25hdone
      Created wheel for spint: filename=spint-1.0.7-cp37-none-any.whl size=31371 sha256=0aaa388fac403080a34d1b9f6b3c0f12bba24f791c59a1accb2ad944551e77ea
      Stored in directory: /root/.cache/pip/wheels/e1/f0/fe/754baccec76ae29184c37ea6112d881a883e044977bd963d08
      Building wheel for spvcm (setup.py) ... [?25l[?25hdone
      Created wheel for spvcm: filename=spvcm-0.3.0-cp37-none-any.whl size=5777202 sha256=17b9c7deab22820963c540135227bd12e4a9353a93f2b2f9fc8604aee8eb7461
      Stored in directory: /root/.cache/pip/wheels/8f/2e/c8/35a9abbb5c8508cfc597cdd2217c1b9b2cb82fc2f7fe18c11c
      Building wheel for splot (setup.py) ... [?25l[?25hdone
      Created wheel for splot: filename=splot-1.1.3-cp37-none-any.whl size=37867 sha256=e7be5e410c9b7745a31ce5684ac5d7868486b1ad547f2492086c0e84e6593de4
      Stored in directory: /root/.cache/pip/wheels/bd/4f/94/71caf6a544f341a1ef2788a7c96272e7e9dfebb04a1aecc24f
    Successfully built pysal inequality pointpats mgwr spglm spint spvcm splot
    [31mERROR: requests 2.23.0 has requirement urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1, but you'll have urllib3 1.26.5 which is incompatible.[0m
    [31mERROR: datascience 0.10.6 has requirement folium==0.2.1, but you'll have folium 0.8.3 which is incompatible.[0m
    [31mERROR: albumentations 0.1.12 has requirement imgaug<0.2.7,>=0.2.5, but you'll have imgaug 0.2.9 which is incompatible.[0m
    [31mERROR: pytest-cov 2.12.1 has requirement coverage>=5.2.1, but you'll have coverage 3.7.1 which is incompatible.[0m
    [31mERROR: pytest-cov 2.12.1 has requirement pytest>=4.6, but you'll have pytest 3.6.4 which is incompatible.[0m
    Installing collected packages: libpysal, access, esda, quantecon, mapclassify, giddy, inequality, opencv-contrib-python, pointpats, munch, click-plugins, cligj, fiona, pyproj, geopandas, segregation, rtree, spaghetti, spreg, spglm, mgwr, spint, spvcm, snuggs, affine, rasterio, pygeos, simplejson, rasterstats, tobler, splot, amply, pulp, spopt, urllib3, python-dateutil, pytest-cov, pysal
      Found existing installation: opencv-contrib-python 4.1.2.30
        Uninstalling opencv-contrib-python-4.1.2.30:
          Successfully uninstalled opencv-contrib-python-4.1.2.30
      Found existing installation: urllib3 1.24.3
        Uninstalling urllib3-1.24.3:
          Successfully uninstalled urllib3-1.24.3
      Found existing installation: python-dateutil 2.8.1
        Uninstalling python-dateutil-2.8.1:
          Successfully uninstalled python-dateutil-2.8.1
    Successfully installed access-1.1.3 affine-2.3.0 amply-0.1.4 click-plugins-1.1.1 cligj-0.7.2 esda-2.3.6 fiona-1.8.20 geopandas-0.9.0 giddy-2.3.3 inequality-1.0.0 libpysal-4.4.0 mapclassify-2.4.2 mgwr-2.1.2 munch-2.5.0 opencv-contrib-python-4.5.2.52 pointpats-2.2.0 pulp-2.4 pygeos-0.10 pyproj-3.1.0 pysal-2.4.0 pytest-cov-2.12.1 python-dateutil-2.8.0 quantecon-0.5.0 rasterio-1.2.4 rasterstats-0.15.0 rtree-0.9.7 segregation-1.5.0 simplejson-3.17.2 snuggs-1.4.7 spaghetti-1.5.6 spglm-1.0.8 spint-1.0.7 splot-1.1.3 spopt-0.1.1 spreg-1.2.2 spvcm-0.3.0 tobler-0.7.0 urllib3-1.26.5




    Collecting cartoframes
    [?25l  Downloading https://files.pythonhosted.org/packages/a2/34/e20671c9b56b9d174078fa0556be3b7f848a98174cd5e81e12d8bcc63359/cartoframes-1.2.1-py2.py3-none-any.whl (244kB)
    [K     |████████████████████████████████| 245kB 8.4MB/s eta 0:00:01
    [?25hRequirement already satisfied: geopandas<1.0,>=0.6.0 in /usr/local/lib/python3.7/dist-packages (from cartoframes) (0.9.0)
    Requirement already satisfied: appdirs<2.0,>=1.4.3 in /usr/local/lib/python3.7/dist-packages (from cartoframes) (1.4.4)
    Collecting semantic-version<3,>=2.8.0
      Downloading https://files.pythonhosted.org/packages/a5/15/00ef3b7888a10363b7c402350eda3acf395ff05bebae312d1296e528516a/semantic_version-2.8.5-py2.py3-none-any.whl
    Collecting carto<2.0,>=1.11.2
      Downloading https://files.pythonhosted.org/packages/25/e1/d32f14e5827b818aec6509b03fc04867728440035a54878d08c108890a1e/carto-1.11.2-py3-none-any.whl
    Requirement already satisfied: jinja2<3.0,>=2.10.1 in /usr/local/lib/python3.7/dist-packages (from cartoframes) (2.11.3)
    Collecting unidecode<2.0,>=1.1.0
    [?25l  Downloading https://files.pythonhosted.org/packages/9e/25/723487ca2a52ebcee88a34d7d1f5a4b80b793f179ee0f62d5371938dfa01/Unidecode-1.2.0-py2.py3-none-any.whl (241kB)
    [K     |████████████████████████████████| 245kB 29.4MB/s 
    [?25hRequirement already satisfied: pandas>=0.25.0 in /usr/local/lib/python3.7/dist-packages (from cartoframes) (1.1.5)
    Requirement already satisfied: shapely>=1.6 in /usr/local/lib/python3.7/dist-packages (from geopandas<1.0,>=0.6.0->cartoframes) (1.7.1)
    Requirement already satisfied: fiona>=1.8 in /usr/local/lib/python3.7/dist-packages (from geopandas<1.0,>=0.6.0->cartoframes) (1.8.20)
    Requirement already satisfied: pyproj>=2.2.0 in /usr/local/lib/python3.7/dist-packages (from geopandas<1.0,>=0.6.0->cartoframes) (3.1.0)
    Requirement already satisfied: requests>=2.7.0 in /usr/local/lib/python3.7/dist-packages (from carto<2.0,>=1.11.2->cartoframes) (2.23.0)
    Collecting pyrestcli==0.6.11
      Downloading https://files.pythonhosted.org/packages/af/24/d3e7638e30f36396caa4ddc1e25d3f1b5ff76d91738166996e74a9cb4fc0/pyrestcli-0.6.11.tar.gz
    Requirement already satisfied: MarkupSafe>=0.23 in /usr/local/lib/python3.7/dist-packages (from jinja2<3.0,>=2.10.1->cartoframes) (2.0.1)
    Requirement already satisfied: pytz>=2017.2 in /usr/local/lib/python3.7/dist-packages (from pandas>=0.25.0->cartoframes) (2018.9)
    Requirement already satisfied: python-dateutil>=2.7.3 in /usr/local/lib/python3.7/dist-packages (from pandas>=0.25.0->cartoframes) (2.8.0)
    Requirement already satisfied: numpy>=1.15.4 in /usr/local/lib/python3.7/dist-packages (from pandas>=0.25.0->cartoframes) (1.19.5)
    Requirement already satisfied: certifi in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (2020.12.5)
    Requirement already satisfied: attrs>=17 in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (21.2.0)
    Requirement already satisfied: click>=4.0 in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (7.1.2)
    Requirement already satisfied: six>=1.7 in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (1.15.0)
    Requirement already satisfied: munch in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (2.5.0)
    Requirement already satisfied: cligj>=0.5 in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (0.7.2)
    Requirement already satisfied: click-plugins>=1.0 in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (1.1.1)
    Requirement already satisfied: setuptools in /usr/local/lib/python3.7/dist-packages (from fiona>=1.8->geopandas<1.0,>=0.6.0->cartoframes) (56.1.0)
    Collecting urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1
    [?25l  Downloading https://files.pythonhosted.org/packages/56/aa/4ef5aa67a9a62505db124a5cb5262332d1d4153462eb8fd89c9fa41e5d92/urllib3-1.25.11-py2.py3-none-any.whl (127kB)
    [K     |████████████████████████████████| 133kB 38.9MB/s 
    [?25hRequirement already satisfied: idna<3,>=2.5 in /usr/local/lib/python3.7/dist-packages (from requests>=2.7.0->carto<2.0,>=1.11.2->cartoframes) (2.10)
    Requirement already satisfied: chardet<4,>=3.0.2 in /usr/local/lib/python3.7/dist-packages (from requests>=2.7.0->carto<2.0,>=1.11.2->cartoframes) (3.0.4)
    Requirement already satisfied: future>=0.15.2 in /usr/local/lib/python3.7/dist-packages (from pyrestcli==0.6.11->carto<2.0,>=1.11.2->cartoframes) (0.16.0)
    Building wheels for collected packages: pyrestcli
      Building wheel for pyrestcli (setup.py) ... [?25l[?25hdone
      Created wheel for pyrestcli: filename=pyrestcli-0.6.11-cp37-none-any.whl size=8500 sha256=059b27982261a0e0d84cd8066b5807f22b318e373ff1c675d8894cba9279d514
      Stored in directory: /root/.cache/pip/wheels/2f/bb/11/396a62e2d1e718f2bfb02b66726240fbc8d98640bfc0cf1688
    Successfully built pyrestcli
    [31mERROR: pysal 2.4.0 has requirement urllib3>=1.26, but you'll have urllib3 1.25.11 which is incompatible.[0m
    [31mERROR: datascience 0.10.6 has requirement folium==0.2.1, but you'll have folium 0.8.3 which is incompatible.[0m
    Installing collected packages: semantic-version, pyrestcli, carto, unidecode, cartoframes, urllib3
      Found existing installation: urllib3 1.26.5
        Uninstalling urllib3-1.26.5:
          Successfully uninstalled urllib3-1.26.5
    Successfully installed carto-1.11.2 cartoframes-1.2.1 pyrestcli-0.6.11 semantic-version-2.8.5 unidecode-1.2.0 urllib3-1.25.11
    Collecting urllib3==1.22
    [?25l  Downloading https://files.pythonhosted.org/packages/63/cb/6965947c13a94236f6d4b8223e21beb4d576dc72e8130bd7880f600839b8/urllib3-1.22-py2.py3-none-any.whl (132kB)
    [K     |████████████████████████████████| 133kB 9.0MB/s 
    [31mERROR: pysal 2.4.0 has requirement urllib3>=1.26, but you'll have urllib3 1.22 which is incompatible.[0m
    [31mERROR: datascience 0.10.6 has requirement folium==0.2.1, but you'll have folium 0.8.3 which is incompatible.[0m
    [?25hInstalling collected packages: urllib3
    Successfully installed urllib3-1.22


Remember to restart the runtime to load correctly the installed libraries!

Now, we download from the web the dataset for this lab.


```python
! wget https://geodacenter.github.io/data-and-lab//data/columbus.zip
! unzip columbus.zip
! wget https://geodacenter.github.io/data-and-lab//data/boston.zip
! unzip boston.zip
! wget https://geodacenter.github.io/data-and-lab//data/kingcounty.zip
! unzip kingcounty.zip
! wget https://github.com/vincnardelli/seai2021/raw/main/lab2/data/dataNUTS3.zip
! unzip dataNUTS3.zip
```

    --2021-06-02 16:01:39--  https://geodacenter.github.io/data-and-lab//data/columbus.zip
    Resolving geodacenter.github.io (geodacenter.github.io)... 185.199.108.153, 185.199.109.153, 185.199.110.153, ...
    Connecting to geodacenter.github.io (geodacenter.github.io)|185.199.108.153|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 472230 (461K) [application/zip]
    Saving to: ‘columbus.zip’
    
    columbus.zip        100%[===================>] 461.16K  --.-KB/s    in 0.02s   
    
    2021-06-02 16:01:39 (18.8 MB/s) - ‘columbus.zip’ saved [472230/472230]
    
    Archive:  columbus.zip
       creating: columbus/
      inflating: columbus/.DS_Store      
       creating: __MACOSX/
       creating: __MACOSX/columbus/
      inflating: __MACOSX/columbus/._.DS_Store  
      inflating: columbus/columbus.csv   
      inflating: __MACOSX/columbus/._columbus.csv  
      inflating: columbus/columbus.dbf   
      inflating: __MACOSX/columbus/._columbus.dbf  
       creating: columbus/columbus.gdb/
      inflating: columbus/columbus.gdb/a00000001.gdbindexes  
      inflating: columbus/columbus.gdb/a00000001.gdbtable  
      inflating: columbus/columbus.gdb/a00000001.gdbtablx  
      inflating: columbus/columbus.gdb/a00000001.TablesByName.atx  
      inflating: columbus/columbus.gdb/a00000002.gdbtable  
      inflating: columbus/columbus.gdb/a00000002.gdbtablx  
      inflating: columbus/columbus.gdb/a00000003.gdbindexes  
      inflating: columbus/columbus.gdb/a00000003.gdbtable  
      inflating: columbus/columbus.gdb/a00000003.gdbtablx  
      inflating: columbus/columbus.gdb/a00000004.CatItemsByPhysicalName.atx  
      inflating: columbus/columbus.gdb/a00000004.CatItemsByType.atx  
      inflating: columbus/columbus.gdb/a00000004.FDO_UUID.atx  
      inflating: columbus/columbus.gdb/a00000004.gdbindexes  
      inflating: columbus/columbus.gdb/a00000004.gdbtable  
      inflating: columbus/columbus.gdb/a00000004.gdbtablx  
      inflating: columbus/columbus.gdb/a00000004.spx  
      inflating: columbus/columbus.gdb/a00000005.CatItemTypesByName.atx  
      inflating: columbus/columbus.gdb/a00000005.CatItemTypesByParentTypeID.atx  
      inflating: columbus/columbus.gdb/a00000005.CatItemTypesByUUID.atx  
      inflating: columbus/columbus.gdb/a00000005.gdbindexes  
      inflating: columbus/columbus.gdb/a00000005.gdbtable  
      inflating: columbus/columbus.gdb/a00000005.gdbtablx  
      inflating: columbus/columbus.gdb/a00000006.CatRelsByDestinationID.atx  
      inflating: columbus/columbus.gdb/a00000006.CatRelsByOriginID.atx  
      inflating: columbus/columbus.gdb/a00000006.CatRelsByType.atx  
      inflating: columbus/columbus.gdb/a00000006.FDO_UUID.atx  
      inflating: columbus/columbus.gdb/a00000006.gdbindexes  
      inflating: columbus/columbus.gdb/a00000006.gdbtable  
      inflating: columbus/columbus.gdb/a00000006.gdbtablx  
      inflating: columbus/columbus.gdb/a00000007.CatRelTypesByBackwardLabel.atx  
      inflating: columbus/columbus.gdb/a00000007.CatRelTypesByDestItemTypeID.atx  
      inflating: columbus/columbus.gdb/a00000007.CatRelTypesByForwardLabel.atx  
      inflating: columbus/columbus.gdb/a00000007.CatRelTypesByName.atx  
      inflating: columbus/columbus.gdb/a00000007.CatRelTypesByOriginItemTypeID.atx  
      inflating: columbus/columbus.gdb/a00000007.CatRelTypesByUUID.atx  
      inflating: columbus/columbus.gdb/a00000007.gdbindexes  
      inflating: columbus/columbus.gdb/a00000007.gdbtable  
      inflating: columbus/columbus.gdb/a00000007.gdbtablx  
      inflating: columbus/columbus.gdb/a00000009.gdbindexes  
      inflating: columbus/columbus.gdb/a00000009.gdbtable  
      inflating: columbus/columbus.gdb/a00000009.gdbtablx  
      inflating: columbus/columbus.gdb/a00000009.spx  
      inflating: columbus/columbus.gdb/gdb  
      inflating: columbus/columbus.gdb/timestamps  
      inflating: columbus/columbus.geojson  
      inflating: columbus/columbus.gpkg  
      inflating: columbus/columbus.html  
      inflating: __MACOSX/columbus/._columbus.html  
      inflating: columbus/columbus.kml   
      inflating: columbus/columbus.mid   
      inflating: columbus/columbus.mif   
      inflating: columbus/columbus.prj   
      inflating: columbus/columbus.shp   
      inflating: __MACOSX/columbus/._columbus.shp  
      inflating: columbus/columbus.shx   
      inflating: __MACOSX/columbus/._columbus.shx  
      inflating: columbus/columbus.sqlite  
      inflating: columbus/columbus.xlsx  
      inflating: __MACOSX/columbus/._columbus.xlsx  
      inflating: __MACOSX/._columbus     
    --2021-06-02 16:01:39--  https://geodacenter.github.io/data-and-lab//data/boston.zip
    Resolving geodacenter.github.io (geodacenter.github.io)... 185.199.108.153, 185.199.109.153, 185.199.110.153, ...
    Connecting to geodacenter.github.io (geodacenter.github.io)|185.199.108.153|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 670702 (655K) [application/zip]
    Saving to: ‘boston.zip’
    
    boston.zip          100%[===================>] 654.98K  --.-KB/s    in 0.03s   
    
    2021-06-02 16:01:39 (18.8 MB/s) - ‘boston.zip’ saved [670702/670702]
    
    Archive:  boston.zip
       creating: boston/
      inflating: boston/.DS_Store        
       creating: __MACOSX/boston/
      inflating: __MACOSX/boston/._.DS_Store  
      inflating: boston/boston.csv       
      inflating: boston/boston.dbf       
      inflating: __MACOSX/boston/._boston.dbf  
      inflating: boston/boston.geojson   
      inflating: boston/boston.gml       
      inflating: boston/boston.gpkg      
      inflating: boston/boston.mid       
      inflating: boston/boston.mif       
      inflating: boston/boston.shp       
      inflating: __MACOSX/boston/._boston.shp  
      inflating: boston/boston.shx       
      inflating: __MACOSX/boston/._boston.shx  
      inflating: boston/boston.sqlite    
      inflating: boston/boston.txt       
      inflating: __MACOSX/boston/._boston.txt  
      inflating: boston/boston.xlsx      
      inflating: boston/boston.xsd       
      inflating: boston/boston_metadata.html  
      inflating: __MACOSX/boston/._boston_metadata.html  
      inflating: boston/style.css        
      inflating: __MACOSX/boston/._style.css  
      inflating: __MACOSX/._boston       
    --2021-06-02 16:01:40--  https://geodacenter.github.io/data-and-lab//data/kingcounty.zip
    Resolving geodacenter.github.io (geodacenter.github.io)... 185.199.108.153, 185.199.109.153, 185.199.110.153, ...
    Connecting to geodacenter.github.io (geodacenter.github.io)|185.199.108.153|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 4061729 (3.9M) [application/zip]
    Saving to: ‘kingcounty.zip’
    
    kingcounty.zip      100%[===================>]   3.87M  --.-KB/s    in 0.1s    
    
    2021-06-02 16:01:40 (34.9 MB/s) - ‘kingcounty.zip’ saved [4061729/4061729]
    
    Archive:  kingcounty.zip
       creating: kingcounty/
      inflating: kingcounty/kc_house.dbf  
       creating: __MACOSX/kingcounty/
      inflating: __MACOSX/kingcounty/._kc_house.dbf  
      inflating: kingcounty/kc_house.prj  
      inflating: __MACOSX/kingcounty/._kc_house.prj  
      inflating: kingcounty/kc_house.shp  
      inflating: __MACOSX/kingcounty/._kc_house.shp  
      inflating: kingcounty/kc_house.shx  
      inflating: __MACOSX/kingcounty/._kc_house.shx  
      inflating: kingcounty/kc_house_data.csv  
      inflating: __MACOSX/kingcounty/._kc_house_data.csv  
      inflating: kingcounty/King_county_zip.dbf  
      inflating: __MACOSX/kingcounty/._King_county_zip.dbf  
      inflating: kingcounty/King_county_zip.geojson  
      inflating: __MACOSX/kingcounty/._King_county_zip.geojson  
      inflating: kingcounty/King_county_zip.prj  
      inflating: __MACOSX/kingcounty/._King_county_zip.prj  
      inflating: kingcounty/King_county_zip.shp  
      inflating: __MACOSX/kingcounty/._King_county_zip.shp  
      inflating: kingcounty/King_county_zip.shx  
      inflating: __MACOSX/kingcounty/._King_county_zip.shx  
      inflating: __MACOSX/._kingcounty   
    --2021-06-02 16:01:40--  https://github.com/vincnardelli/seai2021/raw/main/lab2/data/dataNUTS3.zip
    Resolving github.com (github.com)... 192.30.255.112
    Connecting to github.com (github.com)|192.30.255.112|:443... connected.
    HTTP request sent, awaiting response... 302 Found
    Location: https://raw.githubusercontent.com/vincnardelli/seai2021/main/lab2/data/dataNUTS3.zip [following]
    --2021-06-02 16:01:41--  https://raw.githubusercontent.com/vincnardelli/seai2021/main/lab2/data/dataNUTS3.zip
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.108.133, 185.199.109.133, 185.199.110.133, ...
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.108.133|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 2507426 (2.4M) [application/zip]
    Saving to: ‘dataNUTS3.zip’
    
    dataNUTS3.zip       100%[===================>]   2.39M  --.-KB/s    in 0.08s   
    
    2021-06-02 16:01:41 (30.4 MB/s) - ‘dataNUTS3.zip’ saved [2507426/2507426]
    
    Archive:  dataNUTS3.zip
       creating: dataNUTS3/
      inflating: __MACOSX/._dataNUTS3    
      inflating: dataNUTS3/dataNUTS3.csv  
      inflating: dataNUTS3/NUTS_RG_10M_2013.dbf  
      inflating: __MACOSX/dataNUTS3/._NUTS_RG_10M_2013.dbf  
      inflating: dataNUTS3/NUTS_RG_10M_2013.sbx  
      inflating: __MACOSX/dataNUTS3/._NUTS_RG_10M_2013.sbx  
      inflating: dataNUTS3/NUTS_RG_10M_2013.shx  
      inflating: __MACOSX/dataNUTS3/._NUTS_RG_10M_2013.shx  
      inflating: dataNUTS3/NUTS_RG_10M_2013.shp.xml  
      inflating: __MACOSX/dataNUTS3/._NUTS_RG_10M_2013.shp.xml  
      inflating: dataNUTS3/NUTS_RG_10M_2013.shp  
      inflating: __MACOSX/dataNUTS3/._NUTS_RG_10M_2013.shp  
      inflating: dataNUTS3/NUTS_RG_10M_2013.sbn  
      inflating: __MACOSX/dataNUTS3/._NUTS_RG_10M_2013.sbn  
      inflating: dataNUTS3/NUTS_RG_10M_2013.prj  
      inflating: __MACOSX/dataNUTS3/._NUTS_RG_10M_2013.prj  


Let's start!

# Loading and Plotting spatial data


```python
import pandas as pd
import numpy as np
```


```python
data = pd.read_csv("dataNUTS3/dataNUTS3.csv")
data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NUTS_ID</th>
      <th>year</th>
      <th>alpine</th>
      <th>category</th>
      <th>pcgdp</th>
      <th>employ_1564</th>
      <th>employ_1564_male</th>
      <th>employ_1564_female</th>
      <th>employ_5564</th>
      <th>unempl</th>
      <th>educ_2564</th>
      <th>fertility</th>
      <th>pop</th>
      <th>pop_dens</th>
      <th>ppopGE65</th>
      <th>ppopLT15</th>
      <th>research_exp</th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AT113</td>
      <td>1977</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AT112</td>
      <td>1977</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AT111</td>
      <td>1977</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AT111</td>
      <td>1978</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AT112</td>
      <td>1978</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
  </tbody>
</table>
</div>




```python
data = data.loc[data['year']==2012]
data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NUTS_ID</th>
      <th>year</th>
      <th>alpine</th>
      <th>category</th>
      <th>pcgdp</th>
      <th>employ_1564</th>
      <th>employ_1564_male</th>
      <th>employ_1564_female</th>
      <th>employ_5564</th>
      <th>unempl</th>
      <th>educ_2564</th>
      <th>fertility</th>
      <th>pop</th>
      <th>pop_dens</th>
      <th>ppopGE65</th>
      <th>ppopLT15</th>
      <th>research_exp</th>
      <th>state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>105</th>
      <td>AT111</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>20600.0</td>
      <td>70.4</td>
      <td>75.9</td>
      <td>64.8</td>
      <td>38.7</td>
      <td>4.6</td>
      <td>13.9</td>
      <td>1.30</td>
      <td>37561.0</td>
      <td>54.1</td>
      <td>0.210884</td>
      <td>0.126993</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>106</th>
      <td>AT113</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>22900.0</td>
      <td>70.4</td>
      <td>75.9</td>
      <td>64.8</td>
      <td>38.7</td>
      <td>4.6</td>
      <td>13.9</td>
      <td>1.30</td>
      <td>97721.0</td>
      <td>67.4</td>
      <td>0.200735</td>
      <td>0.128099</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>107</th>
      <td>AT112</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>28500.0</td>
      <td>70.4</td>
      <td>75.9</td>
      <td>64.8</td>
      <td>38.7</td>
      <td>4.6</td>
      <td>13.9</td>
      <td>1.30</td>
      <td>150500.0</td>
      <td>99.0</td>
      <td>0.187960</td>
      <td>0.136744</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>362</th>
      <td>AT127</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly urban</td>
      <td>43200.0</td>
      <td>72.6</td>
      <td>77.2</td>
      <td>68.1</td>
      <td>42.9</td>
      <td>4.6</td>
      <td>17.2</td>
      <td>1.49</td>
      <td>320945.0</td>
      <td>223.1</td>
      <td>0.186381</td>
      <td>0.147617</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
    <tr>
      <th>363</th>
      <td>AT124</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>25300.0</td>
      <td>72.6</td>
      <td>77.2</td>
      <td>68.1</td>
      <td>42.9</td>
      <td>4.6</td>
      <td>17.2</td>
      <td>1.49</td>
      <td>219354.0</td>
      <td>48.1</td>
      <td>0.206958</td>
      <td>0.135202</td>
      <td>NaN</td>
      <td>AT</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>pcgdp</th>
      <th>employ_1564</th>
      <th>employ_1564_male</th>
      <th>employ_1564_female</th>
      <th>employ_5564</th>
      <th>unempl</th>
      <th>educ_2564</th>
      <th>fertility</th>
      <th>pop</th>
      <th>pop_dens</th>
      <th>ppopGE65</th>
      <th>ppopLT15</th>
      <th>research_exp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1474.0</td>
      <td>1240.000000</td>
      <td>1398.000000</td>
      <td>1398.000000</td>
      <td>1398.000000</td>
      <td>1398.000000</td>
      <td>1397.000000</td>
      <td>1398.000000</td>
      <td>1358.000000</td>
      <td>1.325000e+03</td>
      <td>1372.000000</td>
      <td>1323.000000</td>
      <td>1323.000000</td>
      <td>805.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2012.0</td>
      <td>26665.196617</td>
      <td>65.765379</td>
      <td>71.822532</td>
      <td>59.724535</td>
      <td>51.398641</td>
      <td>8.743522</td>
      <td>26.199928</td>
      <td>1.593675</td>
      <td>4.116850e+05</td>
      <td>437.668659</td>
      <td>0.183848</td>
      <td>0.156838</td>
      <td>1.371652</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.0</td>
      <td>14948.025774</td>
      <td>9.474021</td>
      <td>7.892328</td>
      <td>12.187490</td>
      <td>11.899590</td>
      <td>5.773396</td>
      <td>8.612239</td>
      <td>0.341548</td>
      <td>5.986194e+05</td>
      <td>1019.342152</td>
      <td>0.042279</td>
      <td>0.037709</td>
      <td>1.011049</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2012.0</td>
      <td>1700.000000</td>
      <td>28.300000</td>
      <td>50.500000</td>
      <td>6.500000</td>
      <td>16.200000</td>
      <td>2.700000</td>
      <td>6.300000</td>
      <td>1.060000</td>
      <td>1.070700e+04</td>
      <td>1.200000</td>
      <td>0.026679</td>
      <td>0.088176</td>
      <td>0.070000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2012.0</td>
      <td>18675.000000</td>
      <td>59.300000</td>
      <td>66.900000</td>
      <td>53.500000</td>
      <td>40.700000</td>
      <td>4.800000</td>
      <td>19.300000</td>
      <td>1.370000</td>
      <td>1.490120e+05</td>
      <td>64.175000</td>
      <td>0.161477</td>
      <td>0.134810</td>
      <td>0.750000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2012.0</td>
      <td>25600.000000</td>
      <td>67.050000</td>
      <td>72.800000</td>
      <td>62.600000</td>
      <td>52.800000</td>
      <td>7.400000</td>
      <td>26.400000</td>
      <td>1.460000</td>
      <td>2.702010e+05</td>
      <td>129.400000</td>
      <td>0.187967</td>
      <td>0.149737</td>
      <td>1.190000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2012.0</td>
      <td>31900.000000</td>
      <td>73.600000</td>
      <td>78.200000</td>
      <td>68.800000</td>
      <td>61.850000</td>
      <td>10.300000</td>
      <td>32.200000</td>
      <td>1.830000</td>
      <td>4.993400e+05</td>
      <td>323.125000</td>
      <td>0.212095</td>
      <td>0.170365</td>
      <td>1.630000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2012.0</td>
      <td>138156.096600</td>
      <td>82.200000</td>
      <td>87.800000</td>
      <td>80.500000</td>
      <td>79.100000</td>
      <td>37.000000</td>
      <td>51.200000</td>
      <td>3.800000</td>
      <td>1.362424e+07</td>
      <td>21206.100000</td>
      <td>0.294344</td>
      <td>0.424929</td>
      <td>11.050000</td>
    </tr>
  </tbody>
</table>
</div>




```python
data['category'].describe()
```




    count             1127
    unique               3
    top       Intermediate
    freq               450
    Name: category, dtype: object




```python
data['category'].value_counts()
```




    Intermediate           450
    Predominantly rural    416
    Predominantly urban    261
    Name: category, dtype: int64




```python
data['state'].value_counts()
```




    DE    396
    UK    173
    IT    110
    FR    101
    TR     81
    PL     72
    ES     59
    EL     52
    BE     44
    RO     42
    NL     40
    AT     35
    BG     28
    CH     26
    PT     25
    SE     21
    HR     21
    HU     20
    NO     19
    FI     19
    CZ     14
    SI     12
    DK     11
    LT     10
    SK      8
    MK      8
    IE      8
    LV      6
    EE      5
    MT      2
    IS      2
    LU      1
    CY      1
    LI      1
    ME      1
    Name: state, dtype: int64




```python
import seaborn as sns

data['pop_dens_log'] = np.log(data['pop_dens'])
data['pcgdp_log'] = np.log(data['pcgdp'])

sns.scatterplot(data=data, x="pop_dens_log", y="pcgdp_log")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7fda44434cd0>




![png](seai_lab2_files/seai_lab2_14_1.png)



```python
sns.scatterplot(data=data, x="pop_dens_log", y="pcgdp_log", hue="state", alpha=0.5, s=70, legend= False)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7fda52649c50>




![png](seai_lab2_files/seai_lab2_15_1.png)



```python
sns.lmplot(data=data, x="pop_dens_log", y="pcgdp_log", scatter_kws={'alpha':0.2})
```




    <seaborn.axisgrid.FacetGrid at 0x7fda528d2950>




![png](seai_lab2_files/seai_lab2_16_1.png)


## Areal data
GeoPandas is an open source project to make working with geospatial data in python easier. GeoPandas extends the datatypes used by pandas to allow spatial operations on geometric types. Geometric operations are performed by shapely. Geopandas further depends on fiona for file access and matplotlib for plotting.

https://geopandas.org/

The core data structure in GeoPandas is geopandas.GeoDataFrame, a subclass of pandas.DataFrame able to store geometry columns and perform spatial operations. Geometries are handled by geopandas.GeoSeries, a subclass of pandas.Series. Therefore, your GeoDataFrame is a combination of Series with your data (numerical, boolean, text etc.) and GeoSeries with geometries (points, polygons etc.). You can have as many columns with geometries as you wish, there’s no limit typical for desktop GIS software.

![geopandas.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABJIAAAJkCAYAAABK9gshAAABQWlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGASSCwoyGFhYGDIzSspCnJ3UoiIjFJgf8rAxsDEIADElonJxQWOAQE+QCUMMBoVfLvGwAiiL+uCzOLgZurR+LZWstws0ibn1j41TPUogCsltTgZSP8B4qTkgqISBgbGBCBbubykAMRuAbJFioCOArJngNjpEPYaEDsJwj4AVhMS5AxkXwGyBZIzElOA7CdAtk4Skng6EhtqLwhwhBpZuJpaGhBwKumgJLWiBEQ75xdUFmWmZ5QoOAJDKFXBMy9ZT0fByMDIkIEBFN4Q1Z/FwOHIKHYKIZb9iIHB0pqBgekzQiwhlIFhawwDA682QkxrPgODYCYDw2H+gsSiRLgDGL+xFKcZG0HYPEUMDKw//v//LMvAwL6LgeFv0f//v+f+//93CQMD800GhgOFAIUbW3JZgOCKAAAAimVYSWZNTQAqAAAACAAEARoABQAAAAEAAAA+ARsABQAAAAEAAABGASgAAwAAAAEAAgAAh2kABAAAAAEAAABOAAAAAAAAAJAAAAABAAAAkAAAAAEAA5KGAAcAAAASAAAAeKACAAQAAAABAAAEkqADAAQAAAABAAACZAAAAABBU0NJSQAAAFNjcmVlbnNob3QigL0QAAAACXBIWXMAABYlAAAWJQFJUiTwAAAB12lUWHRYTUw6Y29tLmFkb2JlLnhtcAAAAAAAPHg6eG1wbWV0YSB4bWxuczp4PSJhZG9iZTpuczptZXRhLyIgeDp4bXB0az0iWE1QIENvcmUgNi4wLjAiPgogICA8cmRmOlJERiB4bWxuczpyZGY9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkvMDIvMjItcmRmLXN5bnRheC1ucyMiPgogICAgICA8cmRmOkRlc2NyaXB0aW9uIHJkZjphYm91dD0iIgogICAgICAgICAgICB4bWxuczpleGlmPSJodHRwOi8vbnMuYWRvYmUuY29tL2V4aWYvMS4wLyI+CiAgICAgICAgIDxleGlmOlBpeGVsWURpbWVuc2lvbj42MTI8L2V4aWY6UGl4ZWxZRGltZW5zaW9uPgogICAgICAgICA8ZXhpZjpQaXhlbFhEaW1lbnNpb24+MTE3MDwvZXhpZjpQaXhlbFhEaW1lbnNpb24+CiAgICAgICAgIDxleGlmOlVzZXJDb21tZW50PlNjcmVlbnNob3Q8L2V4aWY6VXNlckNvbW1lbnQ+CiAgICAgIDwvcmRmOkRlc2NyaXB0aW9uPgogICA8L3JkZjpSREY+CjwveDp4bXBtZXRhPgpcfXTZAAAAHGlET1QAAAACAAAAAAAAATIAAAAoAAABMgAAATIAADcLwfz4IQAANtdJREFUeAHs3U+s5ld52PEzMx7GBhMcQBHCjkEq9SKoBclyZWdZabpASiuaDbKEsdSt2bSKXXVXYaWRmn3BkvGmm5pmVymJKowXIyRom7AJXRiIcAkwuMXUtckM8+f2zhgiGT3z3PfcmfPc373PZ6o29Tnv+3ve8zk/pOQbY07t7f8Z/hAgQIAAAQIECBAgQIAAAQIECBA4QOCUkHSAkG0CBAgQIECAAAECBAgQIECAAIGbAkKSF4EAAQIECBAgQIAAAQIECBAgQGAnASFpJyYfIkCAAAECBAgQIECAAAECBAgQEJK8AwQIECBAgAABAgQIECBAgAABAjsJCEk7MfkQAQIECBAgQIAAAQIECBAgQICAkOQdIECAAAECBAgQIECAAAECBAgQ2ElASNqJyYcIECBAgAABAgQIECBAgAABAgSEJO8AAQIECBAgQIAAAQIECBAgQIDATgJC0k5MPkSAAAECBAgQIECAAAECBAgQICAkeQcIECBAgAABAgQIECBAgAABAgR2EhCSdmLyIQIECBAgQIAAAQIECBAgQIAAASHJO0CAAAECBAgQIECAAAECBAgQILCTgJC0E5MPESBAgAABAgQIECBAgAABAgQICEneAQIECBAgQIAAAQIECBAgQIAAgZ0EhKSdmHyIAAECBAgQIECAAAECBAgQIEBASPIOECBAgAABAgQIECBAgAABAgQI7CQgJO3E5EMECBAgQIAAAQIECBAgQIAAAQJCkneAAAECBAgQIECAAAECBAgQIEBgJwEhaScmHyJAgAABAgQIECBAgAABAgQIEBCSvAMECBAgQIAAAQIECBAgQIAAAQI7CQhJOzH5EAECBAgQIECAAAECBAgQIECAgJDkHSBAgAABAgQIECBAgAABAgQIENhJQEjaicmHCNwZgW9+85vjJz/5yZ15mKcQIECAAAECBAi0E/jUpz41Tp8+PX7605+O3//9T7c7vwMTOC4C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)



It's work with .geoJSON or PostGIS too!


```python
import geopandas as gpd
gdf = gpd.read_file("dataNUTS3/NUTS_RG_10M_2013.shp")
gdf
```

    /usr/local/lib/python3.7/dist-packages/geopandas/_compat.py:110: UserWarning: The Shapely GEOS version (3.8.0-CAPI-1.13.1 ) is incompatible with the GEOS version PyGEOS was compiled with (3.9.1-CAPI-1.14.2). Conversions between both will be slow.
      shapely_geos_version, geos_capi_version_string





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NUTS_ID</th>
      <th>STAT_LEVL_</th>
      <th>SHAPE_AREA</th>
      <th>SHAPE_LEN</th>
      <th>geometry</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AT</td>
      <td>0</td>
      <td>10.026017</td>
      <td>23.934459</td>
      <td>POLYGON ((15.15733 48.99178, 15.16025 48.94169...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AT1</td>
      <td>1</td>
      <td>2.850834</td>
      <td>11.222485</td>
      <td>POLYGON ((15.15733 48.99178, 15.16025 48.94169...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AT11</td>
      <td>2</td>
      <td>0.473189</td>
      <td>5.822330</td>
      <td>POLYGON ((17.09271 48.09965, 17.06741 48.03144...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AT111</td>
      <td>3</td>
      <td>0.086556</td>
      <td>1.232223</td>
      <td>POLYGON ((16.64622 47.44660, 16.57575 47.40635...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AT112</td>
      <td>3</td>
      <td>0.212046</td>
      <td>2.811666</td>
      <td>POLYGON ((17.16080 48.00666, 17.09466 47.97087...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1946</th>
      <td>ITI33</td>
      <td>3</td>
      <td>0.305710</td>
      <td>2.834500</td>
      <td>POLYGON ((13.66761 43.43056, 13.74297 43.29415...</td>
    </tr>
    <tr>
      <th>1947</th>
      <td>ITI34</td>
      <td>3</td>
      <td>0.134340</td>
      <td>1.916392</td>
      <td>POLYGON ((13.91552 42.89452, 13.71091 42.84333...</td>
    </tr>
    <tr>
      <th>1948</th>
      <td>ITI35</td>
      <td>3</td>
      <td>0.097793</td>
      <td>1.801067</td>
      <td>POLYGON ((13.84185 43.10317, 13.84945 43.06666...</td>
    </tr>
    <tr>
      <th>1949</th>
      <td>ITI4</td>
      <td>2</td>
      <td>1.879270</td>
      <td>9.269680</td>
      <td>POLYGON ((11.94108 42.68365, 12.03930 42.64881...</td>
    </tr>
    <tr>
      <th>1950</th>
      <td>ITI41</td>
      <td>3</td>
      <td>0.392265</td>
      <td>3.510011</td>
      <td>POLYGON ((11.94108 42.68365, 12.03930 42.64881...</td>
    </tr>
  </tbody>
</table>
<p>1951 rows × 5 columns</p>
</div>




```python
gdf = gdf.merge(data, on="NUTS_ID", how="right")
gdf
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>NUTS_ID</th>
      <th>STAT_LEVL_</th>
      <th>SHAPE_AREA</th>
      <th>SHAPE_LEN</th>
      <th>geometry</th>
      <th>year</th>
      <th>alpine</th>
      <th>category</th>
      <th>pcgdp</th>
      <th>employ_1564</th>
      <th>employ_1564_male</th>
      <th>employ_1564_female</th>
      <th>employ_5564</th>
      <th>unempl</th>
      <th>educ_2564</th>
      <th>fertility</th>
      <th>pop</th>
      <th>pop_dens</th>
      <th>ppopGE65</th>
      <th>ppopLT15</th>
      <th>research_exp</th>
      <th>state</th>
      <th>pop_dens_log</th>
      <th>pcgdp_log</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AT111</td>
      <td>3</td>
      <td>0.086556</td>
      <td>1.232223</td>
      <td>POLYGON ((16.64622 47.44660, 16.57575 47.40635...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>20600.0</td>
      <td>70.4</td>
      <td>75.9</td>
      <td>64.8</td>
      <td>38.7</td>
      <td>4.6</td>
      <td>13.9</td>
      <td>1.30</td>
      <td>37561.0</td>
      <td>54.1</td>
      <td>0.210884</td>
      <td>0.126993</td>
      <td>NaN</td>
      <td>AT</td>
      <td>3.990834</td>
      <td>9.933046</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AT113</td>
      <td>3</td>
      <td>0.174587</td>
      <td>2.299135</td>
      <td>POLYGON ((16.43376 47.35292, 16.48374 47.28760...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>22900.0</td>
      <td>70.4</td>
      <td>75.9</td>
      <td>64.8</td>
      <td>38.7</td>
      <td>4.6</td>
      <td>13.9</td>
      <td>1.30</td>
      <td>97721.0</td>
      <td>67.4</td>
      <td>0.200735</td>
      <td>0.128099</td>
      <td>NaN</td>
      <td>AT</td>
      <td>4.210645</td>
      <td>10.038892</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AT112</td>
      <td>3</td>
      <td>0.212046</td>
      <td>2.811666</td>
      <td>POLYGON ((17.16080 48.00666, 17.09466 47.97087...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>28500.0</td>
      <td>70.4</td>
      <td>75.9</td>
      <td>64.8</td>
      <td>38.7</td>
      <td>4.6</td>
      <td>13.9</td>
      <td>1.30</td>
      <td>150500.0</td>
      <td>99.0</td>
      <td>0.187960</td>
      <td>0.136744</td>
      <td>NaN</td>
      <td>AT</td>
      <td>4.595120</td>
      <td>10.257659</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AT127</td>
      <td>3</td>
      <td>0.181179</td>
      <td>2.698516</td>
      <td>POLYGON ((17.06674 48.11868, 17.03600 48.08430...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly urban</td>
      <td>43200.0</td>
      <td>72.6</td>
      <td>77.2</td>
      <td>68.1</td>
      <td>42.9</td>
      <td>4.6</td>
      <td>17.2</td>
      <td>1.49</td>
      <td>320945.0</td>
      <td>223.1</td>
      <td>0.186381</td>
      <td>0.147617</td>
      <td>NaN</td>
      <td>AT</td>
      <td>5.407620</td>
      <td>10.673596</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AT124</td>
      <td>3</td>
      <td>0.567886</td>
      <td>3.891105</td>
      <td>POLYGON ((15.54245 48.90770, 15.75363 48.85218...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>25300.0</td>
      <td>72.6</td>
      <td>77.2</td>
      <td>68.1</td>
      <td>42.9</td>
      <td>4.6</td>
      <td>17.2</td>
      <td>1.49</td>
      <td>219354.0</td>
      <td>48.1</td>
      <td>0.206958</td>
      <td>0.135202</td>
      <td>NaN</td>
      <td>AT</td>
      <td>3.873282</td>
      <td>10.138560</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1469</th>
      <td>UKN01</td>
      <td>3</td>
      <td>0.016042</td>
      <td>0.553346</td>
      <td>POLYGON ((-5.91293 54.64804, -5.85534 54.63377...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly urban</td>
      <td>49100.0</td>
      <td>66.0</td>
      <td>69.9</td>
      <td>62.2</td>
      <td>55.9</td>
      <td>7.4</td>
      <td>32.1</td>
      <td>2.03</td>
      <td>280717.0</td>
      <td>2567.4</td>
      <td>0.146104</td>
      <td>0.176997</td>
      <td>1.57</td>
      <td>UK</td>
      <td>7.850649</td>
      <td>10.801614</td>
    </tr>
    <tr>
      <th>1470</th>
      <td>UKN04</td>
      <td>3</td>
      <td>0.450038</td>
      <td>4.684459</td>
      <td>POLYGON ((-5.97653 55.05660, -6.09788 54.98403...</td>
      <td>2012</td>
      <td>No</td>
      <td>Intermediate</td>
      <td>19100.0</td>
      <td>66.0</td>
      <td>69.9</td>
      <td>62.2</td>
      <td>55.9</td>
      <td>7.4</td>
      <td>32.1</td>
      <td>2.03</td>
      <td>289557.0</td>
      <td>90.1</td>
      <td>0.141979</td>
      <td>0.199432</td>
      <td>1.57</td>
      <td>UK</td>
      <td>4.500920</td>
      <td>9.857444</td>
    </tr>
    <tr>
      <th>1471</th>
      <td>UKN03</td>
      <td>3</td>
      <td>0.471958</td>
      <td>6.393123</td>
      <td>MULTIPOLYGON (((-5.99263 54.98926, -5.97045 54...</td>
      <td>2012</td>
      <td>No</td>
      <td>Intermediate</td>
      <td>21500.0</td>
      <td>66.0</td>
      <td>69.9</td>
      <td>62.2</td>
      <td>55.9</td>
      <td>7.4</td>
      <td>32.1</td>
      <td>2.03</td>
      <td>441222.0</td>
      <td>141.1</td>
      <td>0.154099</td>
      <td>0.196744</td>
      <td>1.57</td>
      <td>UK</td>
      <td>4.949469</td>
      <td>9.975808</td>
    </tr>
    <tr>
      <th>1472</th>
      <td>UKN05</td>
      <td>3</td>
      <td>0.902413</td>
      <td>6.631712</td>
      <td>POLYGON ((-6.50002 54.91871, -6.45709 54.82455...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly rural</td>
      <td>20300.0</td>
      <td>66.0</td>
      <td>69.9</td>
      <td>62.2</td>
      <td>55.9</td>
      <td>7.4</td>
      <td>32.1</td>
      <td>2.03</td>
      <td>415192.0</td>
      <td>66.6</td>
      <td>0.133822</td>
      <td>0.213335</td>
      <td>1.57</td>
      <td>UK</td>
      <td>4.198705</td>
      <td>9.918376</td>
    </tr>
    <tr>
      <th>1473</th>
      <td>UKN02</td>
      <td>3</td>
      <td>0.119908</td>
      <td>2.793266</td>
      <td>MULTIPOLYGON (((-5.77064 54.61195, -5.83296 54...</td>
      <td>2012</td>
      <td>No</td>
      <td>Predominantly urban</td>
      <td>19200.0</td>
      <td>66.0</td>
      <td>69.9</td>
      <td>62.2</td>
      <td>55.9</td>
      <td>7.4</td>
      <td>32.1</td>
      <td>2.03</td>
      <td>392247.0</td>
      <td>468.4</td>
      <td>0.162120</td>
      <td>0.188583</td>
      <td>1.57</td>
      <td>UK</td>
      <td>6.149323</td>
      <td>9.862666</td>
    </tr>
  </tbody>
</table>
<p>1474 rows × 24 columns</p>
</div>




```python
gdf.plot(column='pop_dens', cmap='Reds')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7fda2faca810>




![png](seai_lab2_files/seai_lab2_23_1.png)


EQUAL INTERVAL divides the data into equal size classes (e.g., 0-10, 10-20, 20-30, etc.) and works best on data that is generally spread across the entire range. CAUTION: Avoid equal interval if your data are skewed to one end or if you have one or two really large outlier values.


```python
plt = gdf.plot(column='pop_dens', scheme='equal_interval', k=5, cmap='Reds', figsize=(10, 8), edgecolor='black',  linewidth=0.1)
plt.set_xlim(-11, 30)
plt.set_ylim(34, 70);
```


![png](seai_lab2_files/seai_lab2_25_0.png)


NATURAL BREAKS is a kind of “optimal” classification scheme that finds class breaks that will minimize within-class variance and maximize between-class differences. 


```python
plt = gdf.plot(column='pop_dens', scheme='natural_breaks', k=5, cmap='Reds', figsize=(10, 8), edgecolor='black',  linewidth=0.1)
plt.set_xlim(-11, 30)
plt.set_ylim(34, 70);
```


![png](seai_lab2_files/seai_lab2_27_0.png)


QUANTILES will create attractive maps that place an equal number of observations in each class.



```python
plt = gdf.plot(column='pop_dens', scheme='Quantiles', k=5, cmap='Reds',  figsize=(10, 8), edgecolor='black',  linewidth=0.1)
plt.set_xlim(-11, 30)
plt.set_ylim(34, 70);
```


![png](seai_lab2_files/seai_lab2_29_0.png)



```python
plt = gdf.plot(column='pop_dens', scheme='Quantiles', k=7, cmap='Blues',legend=True, figsize=(10, 8), edgecolor='black',  linewidth=0.1)
plt.set_xlim(-11, 30)
plt.set_ylim(34, 70);
```


![png](seai_lab2_files/seai_lab2_30_0.png)


### Interactive plots with Carto Frames

CARTOframes is a Python package for integrating CARTO maps, analysis, and data services into data science workflows.

https://carto.com/developers/cartoframes


```python
from cartoframes.viz import Layer, color_bins_style, formula_widget, category_widget, histogram_widget
Layer(
    gdf,
    color_bins_style('pop_dens', palette='CB_BLUES', bins=5, opacity=0.8)
)
```


    Output hidden; open in https://colab.research.google.com to view.



```python
from cartoframes.viz import Layer, color_bins_style, formula_widget, category_widget, histogram_widget
Layer(
    gdf,
    color_bins_style('pop_dens', palette='CB_BLUES', bins=5, opacity=0.8),
    default_widget=True,
    default_popup_hover=False,
    widgets=[
        formula_widget('pop', 'sum', 'Population'),
        formula_widget('pcgdp', 'sum', 'Per capita GDP'),
        category_widget('category', 'Category'),

        histogram_widget('unempl', 'Population density'),

        histogram_widget('pop_dens', 'Population density'),
        category_widget('category', 'Category'),
        category_widget('alpine', 'Alpine')
    ]
)

```


    Output hidden; open in https://colab.research.google.com to view.


## Point data


```python
kc = gpd.read_file("kingcounty/kc_house.shp")
kc
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_liv</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basmt</th>
      <th>yr_built</th>
      <th>yr_renov</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_liv15</th>
      <th>sqft_lot15</th>
      <th>geometry</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.129301e+09</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>1180.0</td>
      <td>5650.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>7.0</td>
      <td>1180.0</td>
      <td>0.0</td>
      <td>1955.0</td>
      <td>0.0</td>
      <td>98178.0</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340.0</td>
      <td>5650.0</td>
      <td>POINT (-122.25700 47.51120)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6.414100e+09</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>2570.0</td>
      <td>7242.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>7.0</td>
      <td>2170.0</td>
      <td>400.0</td>
      <td>1951.0</td>
      <td>1991.0</td>
      <td>98125.0</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690.0</td>
      <td>7639.0</td>
      <td>POINT (-122.31900 47.72100)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5.631500e+09</td>
      <td>20150225T000000</td>
      <td>180000.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>770.0</td>
      <td>10000.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>770.0</td>
      <td>0.0</td>
      <td>1933.0</td>
      <td>0.0</td>
      <td>98028.0</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720.0</td>
      <td>8062.0</td>
      <td>POINT (-122.23300 47.73790)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2.487201e+09</td>
      <td>20141209T000000</td>
      <td>604000.0</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>1960.0</td>
      <td>5000.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>7.0</td>
      <td>1050.0</td>
      <td>910.0</td>
      <td>1965.0</td>
      <td>0.0</td>
      <td>98136.0</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360.0</td>
      <td>5000.0</td>
      <td>POINT (-122.39300 47.52080)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.954401e+09</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1680.0</td>
      <td>8080.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>8.0</td>
      <td>1680.0</td>
      <td>0.0</td>
      <td>1987.0</td>
      <td>0.0</td>
      <td>98074.0</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800.0</td>
      <td>7503.0</td>
      <td>POINT (-122.04500 47.61680)</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21608</th>
      <td>2.630000e+08</td>
      <td>20140521T000000</td>
      <td>360000.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1530.0</td>
      <td>1131.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>8.0</td>
      <td>1530.0</td>
      <td>0.0</td>
      <td>2009.0</td>
      <td>0.0</td>
      <td>98103.0</td>
      <td>47.6993</td>
      <td>-122.346</td>
      <td>1530.0</td>
      <td>1509.0</td>
      <td>POINT (-122.34600 47.69930)</td>
    </tr>
    <tr>
      <th>21609</th>
      <td>6.600060e+09</td>
      <td>20150223T000000</td>
      <td>400000.0</td>
      <td>4.0</td>
      <td>2.0</td>
      <td>2310.0</td>
      <td>5813.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>8.0</td>
      <td>2310.0</td>
      <td>0.0</td>
      <td>2014.0</td>
      <td>0.0</td>
      <td>98146.0</td>
      <td>47.5107</td>
      <td>-122.362</td>
      <td>1830.0</td>
      <td>7200.0</td>
      <td>POINT (-122.36200 47.51070)</td>
    </tr>
    <tr>
      <th>21610</th>
      <td>1.523300e+09</td>
      <td>20140623T000000</td>
      <td>402101.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>1020.0</td>
      <td>1350.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>7.0</td>
      <td>1020.0</td>
      <td>0.0</td>
      <td>2009.0</td>
      <td>0.0</td>
      <td>98144.0</td>
      <td>47.5944</td>
      <td>-122.299</td>
      <td>1020.0</td>
      <td>2007.0</td>
      <td>POINT (-122.29900 47.59440)</td>
    </tr>
    <tr>
      <th>21611</th>
      <td>2.913101e+08</td>
      <td>20150116T000000</td>
      <td>400000.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1600.0</td>
      <td>2388.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>8.0</td>
      <td>1600.0</td>
      <td>0.0</td>
      <td>2004.0</td>
      <td>0.0</td>
      <td>98027.0</td>
      <td>47.5345</td>
      <td>-122.069</td>
      <td>1410.0</td>
      <td>1287.0</td>
      <td>POINT (-122.06900 47.53450)</td>
    </tr>
    <tr>
      <th>21612</th>
      <td>1.523300e+09</td>
      <td>20141015T000000</td>
      <td>325000.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>1020.0</td>
      <td>1076.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>7.0</td>
      <td>1020.0</td>
      <td>0.0</td>
      <td>2008.0</td>
      <td>0.0</td>
      <td>98144.0</td>
      <td>47.5941</td>
      <td>-122.299</td>
      <td>1020.0</td>
      <td>1357.0</td>
      <td>POINT (-122.29900 47.59410)</td>
    </tr>
  </tbody>
</table>
<p>21613 rows × 22 columns</p>
</div>



Coordinate Reference Systems

A coordinate reference system (CRS) then defines how the two-dimensional, projected map in your GIS relates to real places on the earth. The decision of which map projection and CRS to use depends on the regional extent of the area you want to work in, on the analysis you want to do, and often on the availability of data.

https://datacarpentry.org/organization-geospatial/03-crs/


```python
kc.crs
```




    <Geographic 2D CRS: EPSG:4326>
    Name: WGS 84
    Axis Info [ellipsoidal]:
    - Lat[north]: Geodetic latitude (degree)
    - Lon[east]: Geodetic longitude (degree)
    Area of Use:
    - name: World.
    - bounds: (-180.0, -90.0, 180.0, 90.0)
    Datum: World Geodetic System 1984 ensemble
    - Ellipsoid: WGS 84
    - Prime Meridian: Greenwich



Let's try to do the same starting from non-projected non-spatial dataset from a csv file!


```python
kc = pd.read_csv("kingcounty/kc_house_data.csv")
kc.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>20150225T000000</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>6</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>20141209T000000</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
      <td>7</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
  </tbody>
</table>
</div>




```python
kc = gpd.GeoDataFrame(kc, geometry=gpd.points_from_xy(kc.long, kc.lat, crs=4326))
kc.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>geometry</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
      <td>POINT (-122.25700 47.51120)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
      <td>POINT (-122.31900 47.72100)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>20150225T000000</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>6</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
      <td>POINT (-122.23300 47.73790)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>20141209T000000</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
      <td>7</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
      <td>POINT (-122.39300 47.52080)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
      <td>POINT (-122.04500 47.61680)</td>
    </tr>
  </tbody>
</table>
</div>




```python
kc.plot(column='price', cmap='Reds', legend=True, alpha=0.5, figsize=(10, 6));
```


![png](seai_lab2_files/seai_lab2_41_0.png)



```python
kc.plot(column='price', cmap='coolwarm', legend=True, alpha=0.3, figsize=(10, 6), edgecolor='black',  linewidth=0.2);
```


![png](seai_lab2_files/seai_lab2_42_0.png)



```python
kc.plot(column='price', scheme='Quantiles', k=5, cmap='Reds', legend=True, alpha=0.5, figsize=(10, 6));
```


![png](seai_lab2_files/seai_lab2_43_0.png)



```python
from cartoframes.viz import Layer, color_bins_style, formula_widget, category_widget, histogram_widget, popup_element
Layer(
    kc,
    color_bins_style('price', palette='CB_BLUES', bins=5, opacity=0.8),
    default_widget=True,
    default_popup_hover=False,
    widgets=[
        formula_widget('id', 'count', 'Houses'),
        histogram_widget('sqft_lot', 'Sqft'),
        histogram_widget('bedrooms', 'Bedrooms')],
    popup_hover=[
        popup_element('price'),
        popup_element('bedrooms'),
        popup_element('bathrooms')
    ]
)
```




<iframe
  frameborder="0"
  style="
    border: 1px solid #cfcfcf;
    width: 100%;
    height: 632px;
    "
  srcDoc="
  <!DOCTYPE html>
<html lang=&quot;en&quot;>
<head>
  <title>None</title>
  <meta name=&quot;description&quot; content=&quot;None&quot;>
  <meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
  <meta charset=&quot;UTF-8&quot;>
  <!-- Include CARTO VL JS -->
  <script src=&quot;https://libs.cartocdn.com/carto-vl/v1.4/carto-vl.min.js&quot;></script>
  <!-- Include Mapbox GL JS -->
  <script src=&quot;https://api.tiles.mapbox.com/mapbox-gl-js/v1.0.0/mapbox-gl.js&quot;></script>
  <!-- Include Mapbox GL CSS -->
  <link href=&quot;https://api.tiles.mapbox.com/mapbox-gl-js/v1.0.0/mapbox-gl.css&quot; rel=&quot;stylesheet&quot; />

  <!-- Include Airship -->
  <script nomodule=&quot;&quot; src=&quot;https://libs.cartocdn.com/airship-components/v2.3/airship.js&quot;></script>
  <script type=&quot;module&quot; src=&quot;https://libs.cartocdn.com/airship-components/v2.3/airship/airship.esm.js&quot;></script>
  <script src=&quot;https://libs.cartocdn.com/airship-bridge/v2.3/asbridge.min.js&quot;></script>
  <link href=&quot;https://libs.cartocdn.com/airship-style/v2.3/airship.min.css&quot; rel=&quot;stylesheet&quot;>
  <link href=&quot;https://libs.cartocdn.com/airship-icons/v2.3/icons.css&quot; rel=&quot;stylesheet&quot;>

  <link href=&quot;https://fonts.googleapis.com/css?family=Roboto&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;>

  <!-- External libraries -->

  <!-- pako -->
  <script src=&quot;https://libs.cartocdn.com/cartoframes/dependencies/pako_inflate.min.js&quot;></script>
  
  <!-- html2canvas -->
  

  
  <style>
  body {
    margin: 0;
    padding: 0;
  }

  aside.as-sidebar {
    min-width: 300px;
  }

  .map-image {
    display: none;
    max-width: 100%;
    height: auto;
  }

  as-layer-selector-slot .as-layer-selector-slot--wrapper .as-caption { // FIXME
    font-size: 14px;
    line-height: 14px;
  }
</style>
  <style>
  .map {
    position: absolute;
    height: 100%;
    width: 100%;
  }

  .map-info {
    position: absolute;
    bottom: 0;
    padding: 0 5px;
    background-color: rgba(255, 255, 255, 0.5);
    margin: 0;
    color: rgba(0, 0, 0, 0.75);
    font-size: 12px;
    width: auto;
    height: 18px;
    font-family: 'Open Sans';
  }

  .map-footer {
    background: #F2F6F9;
    font-family: Roboto;
    font-size: 12px;
    line-height: 24px;
    color: #162945;
    text-align: center;
    z-index: 2;
  }

  .map-footer a {
    text-decoration: none;
  }

  .map-footer a:hover {
    text-decoration: underline;
  }
</style>
    <style>
    #error-container {
      position: absolute;
      width: 100%;
      height: 100%;
      background-color: white;
      visibility: hidden;
      padding: 1em;
      font-family: &quot;Courier New&quot;, Courier, monospace;
      margin: 0 auto;
      font-size: 14px;
      overflow: auto;
      z-index: 1000;
      color: black;
    }

    .error-section {
      padding: 1em;
      border-radius: 5px;
      background-color: #fee;
    }

    #error-container #error-highlight {
      font-weight: bold;
      color: inherit;
    }

    #error-container #error-type {
      color: #008000;
    }

    #error-container #error-name {
      color: #ba2121;
    }

    #error-container #error-content {
      margin-top: 0.4em;
    }

    .error-details {
      margin-top: 1em;
    }

    #error-stacktrace {
      list-style: none;
    }
</style>
  <style>
    .popup-content {
      display: flex;
      flex-direction: column;
      padding: 8px;
    }

    .popup-name {
      font-size: 12px;
      font-weight: 400;
      line-height: 20px;
      margin-bottom: 4px;
    }

    .popup-value {
      font-size: 16px;
      font-weight: 600;
      line-height: 20px;
    }

    .popup-value:not(:last-of-type) {
      margin-bottom: 16px;
    }
</style>
  <style>
  as-widget-header .as-widget-header__header {
    margin-bottom: 8px;
    overflow-wrap: break-word;
  }

  as-widget-header .as-widget-header__subheader {
    margin-bottom: 12px;
  }

  as-category-widget {
    max-height: 250px;
  }
</style>
</head>

<body class=&quot;as-app-body as-app&quot;>
  <img id=&quot;map-image&quot; class=&quot;map-image&quot; alt='Static map image' />
  <as-responsive-content id=&quot;main-container&quot;>
    
      

<aside class=&quot;as-sidebar as-sidebar--right&quot; id=&quot;widgets&quot; data-name=&quot;Widgets&quot;>
  
    
      
        
          <div class=&quot;as-box&quot;>
            <section class=&quot;as-body&quot;>
    
      <div>
  <as-widget-header
    header=&quot;Houses&quot;
    subheader=&quot;&quot;>
  </as-widget-header>

  <p class=&quot;as-title as-m--4 as-p--0 as-font--medium&quot; id=&quot;layer0_widget0-value&quot;>
    <span class=&quot;as-loading as-loading--s&quot;>
      <svg viewBox=&quot;0 0 50 50&quot;>
        <circle cx=&quot;25&quot; cy=&quot;25&quot; r=&quot;20&quot; fill=&quot;none&quot; />
      </svg>
    </span>
  </p>

  
</div>
    
  </section>
          </div>
        
          <div class=&quot;as-box&quot;>
            <section class=&quot;as-body&quot;>
    
      <div>
  <as-histogram-widget
    id=&quot;layer0_widget1&quot;
    description=&quot;&quot;
    heading=&quot;Sqft&quot;>
  </as-histogram-widget>
  
</div>
    
  </section>
          </div>
        
          <div class=&quot;as-box&quot;>
            <section class=&quot;as-body&quot;>
    
      <div>
  <as-histogram-widget
    id=&quot;layer0_widget2&quot;
    description=&quot;&quot;
    heading=&quot;Bedrooms&quot;>
  </as-histogram-widget>
  
</div>
    
  </section>
          </div>
        
    
  
</aside>
    
    <main class=&quot;as-main&quot;>
      <div class=&quot;as-map-area&quot;>
        <div id=&quot;map&quot; class=&quot;map&quot;></div>
        
        
          <div class=&quot;as-map-panels&quot; data-name=&quot;Legends&quot;>
            <div class=&quot;as-panel as-panel--vertical as-panel--left as-panel--top&quot;>
              

<div class=&quot;as-panel__element&quot; id=&quot;legends&quot;>
  <as-layer-selector id=&quot;layer-selector&quot;>
    
      
        
        
        <div slot=&quot;as-checkbox-layer-0-slot&quot;>
          
            
              <as-legend
                heading=&quot;price&quot;
                description=&quot;&quot;>
                <as-legend-color-bins id=&quot;layer0_map0_legend0&quot; slot=&quot;legends&quot;></as-legend-color-bins>
                
              </as-legend>
            
          
        </div>
      
    
  </as-layer-selector>
</div>
            </div> <!-- as-panel -->
          </div> <!-- as-map-panels -->
        
      </div> <!-- as-map-area -->
    </main> <!-- as-main -->
  </as-responsive-content>

  

  <div id=&quot;error-container&quot; class=&quot;error&quot;>
  <section class=&quot;error-section&quot;>
    <span class=&quot;errors&quot; id=&quot;error-name&quot;></span>:
    <section id=&quot;error-content&quot;>
      <span class=&quot;errors&quot; id=&quot;error-type&quot;></span>
      <span class=&quot;errors&quot; id=&quot;error-message&quot;></span>
    </section>
  </section>

  <details class=&quot;error-details&quot;>
    <summary>StackTrace</summary>
    <ul id=&quot;error-stacktrace&quot;></ul>
  </details>
</div>
</body>

<script>
  var init = (function () {
  'use strict';

  const BASEMAPS = {
    DarkMatter: carto.basemaps.darkmatter,
    Voyager: carto.basemaps.voyager,
    Positron: carto.basemaps.positron
  };

  const attributionControl = new mapboxgl.AttributionControl({
    compact: false
  });

  const FIT_BOUNDS_SETTINGS = { animate: false, padding: 50, maxZoom: 16 };

  /** From https://github.com/errwischt/stacktrace-parser/blob/master/src/stack-trace-parser.js */

  /**
   * This parses the different stack traces and puts them into one format
   * This borrows heavily from TraceKit (https://github.com/csnover/TraceKit)
   */

  const UNKNOWN_FUNCTION = '<unknown>';
  const chromeRe = /^\s*at (.*?) ?\(((?:file|https?|blob|chrome-extension|native|eval|webpack|<anonymous>|\/).*?)(?::(\d+))?(?::(\d+))?\)?\s*$/i;
  const chromeEvalRe = /\((\S*)(?::(\d+))(?::(\d+))\)/;
  const winjsRe = /^\s*at (?:((?:\[object object\])?.+) )?\(?((?:file|ms-appx|https?|webpack|blob):.*?):(\d+)(?::(\d+))?\)?\s*$/i;
  const geckoRe = /^\s*(.*?)(?:\((.*?)\))?(?:^|@)((?:file|https?|blob|chrome|webpack|resource|\[native).*?|[^@]*bundle)(?::(\d+))?(?::(\d+))?\s*$/i;
  const geckoEvalRe = /(\S+) line (\d+)(?: > eval line \d+)* > eval/i;

  function parse(stackString) {
    const lines = stackString.split('\n');

    return lines.reduce((stack, line) => {
      const parseResult =
        parseChrome(line) ||
        parseWinjs(line) ||
        parseGecko(line);

      if (parseResult) {
        stack.push(parseResult);
      }

      return stack;
    }, []);
  }

  function parseChrome(line) {
    const parts = chromeRe.exec(line);

    if (!parts) {
      return null;
    }

    const isNative = parts[2] && parts[2].indexOf('native') === 0; // start of line
    const isEval = parts[2] && parts[2].indexOf('eval') === 0; // start of line

    const submatch = chromeEvalRe.exec(parts[2]);
    if (isEval && submatch != null) {
      // throw out eval line/column and use top-most line/column number
      parts[2] = submatch[1]; // url
      parts[3] = submatch[2]; // line
      parts[4] = submatch[3]; // column
    }

    return {
      file: !isNative ? parts[2] : null,
      methodName: parts[1] || UNKNOWN_FUNCTION,
      arguments: isNative ? [parts[2]] : [],
      lineNumber: parts[3] ? +parts[3] : null,
      column: parts[4] ? +parts[4] : null,
    };
  }

  function parseWinjs(line) {
    const parts = winjsRe.exec(line);

    if (!parts) {
      return null;
    }

    return {
      file: parts[2],
      methodName: parts[1] || UNKNOWN_FUNCTION,
      arguments: [],
      lineNumber: +parts[3],
      column: parts[4] ? +parts[4] : null,
    };
  }

  function parseGecko(line) {
    const parts = geckoRe.exec(line);

    if (!parts) {
      return null;
    }

    const isEval = parts[3] && parts[3].indexOf(' > eval') > -1;

    const submatch = geckoEvalRe.exec(parts[3]);
    if (isEval && submatch != null) {
      // throw out eval line/column and use top-most line number
      parts[3] = submatch[1];
      parts[4] = submatch[2];
      parts[5] = null; // no column when eval
    }

    return {
      file: parts[3],
      methodName: parts[1] || UNKNOWN_FUNCTION,
      arguments: parts[2] ? parts[2].split(',') : [],
      lineNumber: parts[4] ? +parts[4] : null,
      column: parts[5] ? +parts[5] : null,
    };
  }

  function displayError(e) {
    const error$ = document.getElementById('error-container');
    const errors$ = error$.getElementsByClassName('errors');
    const stacktrace$ = document.getElementById('error-stacktrace');

    errors$[0].innerHTML = e.name;
    errors$[1].innerHTML = e.type;
    errors$[2].innerHTML = e.message.replace(e.type, '');

    error$.style.visibility = 'visible';

    const stack = parse(e.stack);
    const list = stack.map(item => {
      return `<li>
      at <span class=&quot;stacktrace-method&quot;>${item.methodName}:</span>
      (${item.file}:${item.lineNumber}:${item.column})
    </li>`;
    });

    stacktrace$.innerHTML = list.join('\n');
  }

  // Computes the decimal coefficient and exponent of the specified number x with
  // significant digits p, where x is positive and p is in [1, 21] or undefined.
  // For example, formatDecimal(1.23) returns [&quot;123&quot;, 0].
  function formatDecimal(x, p) {
    if ((i = (x = p ? x.toExponential(p - 1) : x.toExponential()).indexOf(&quot;e&quot;)) < 0) return null; // NaN, ±Infinity
    var i, coefficient = x.slice(0, i);

    // The string returned by toExponential either has the form \d\.\d+e[-+]\d+
    // (e.g., 1.2e+3) or the form \de[-+]\d+ (e.g., 1e+3).
    return [
      coefficient.length > 1 ? coefficient[0] + coefficient.slice(2) : coefficient,
      +x.slice(i + 1)
    ];
  }

  function exponent(x) {
    return x = formatDecimal(Math.abs(x)), x ? x[1] : NaN;
  }

  function formatGroup(grouping, thousands) {
    return function(value, width) {
      var i = value.length,
          t = [],
          j = 0,
          g = grouping[0],
          length = 0;

      while (i > 0 && g > 0) {
        if (length + g + 1 > width) g = Math.max(1, width - length);
        t.push(value.substring(i -= g, i + g));
        if ((length += g + 1) > width) break;
        g = grouping[j = (j + 1) % grouping.length];
      }

      return t.reverse().join(thousands);
    };
  }

  function formatNumerals(numerals) {
    return function(value) {
      return value.replace(/[0-9]/g, function(i) {
        return numerals[+i];
      });
    };
  }

  // [[fill]align][sign][symbol][0][width][,][.precision][~][type]
  var re = /^(?:(.)?([<>=^]))?([+\-( ])?([$#])?(0)?(\d+)?(,)?(\.\d+)?(~)?([a-z%])?$/i;

  function formatSpecifier(specifier) {
    if (!(match = re.exec(specifier))) throw new Error(&quot;invalid format: &quot; + specifier);
    var match;
    return new FormatSpecifier({
      fill: match[1],
      align: match[2],
      sign: match[3],
      symbol: match[4],
      zero: match[5],
      width: match[6],
      comma: match[7],
      precision: match[8] && match[8].slice(1),
      trim: match[9],
      type: match[10]
    });
  }

  formatSpecifier.prototype = FormatSpecifier.prototype; // instanceof

  function FormatSpecifier(specifier) {
    this.fill = specifier.fill === undefined ? &quot; &quot; : specifier.fill + &quot;&quot;;
    this.align = specifier.align === undefined ? &quot;>&quot; : specifier.align + &quot;&quot;;
    this.sign = specifier.sign === undefined ? &quot;-&quot; : specifier.sign + &quot;&quot;;
    this.symbol = specifier.symbol === undefined ? &quot;&quot; : specifier.symbol + &quot;&quot;;
    this.zero = !!specifier.zero;
    this.width = specifier.width === undefined ? undefined : +specifier.width;
    this.comma = !!specifier.comma;
    this.precision = specifier.precision === undefined ? undefined : +specifier.precision;
    this.trim = !!specifier.trim;
    this.type = specifier.type === undefined ? &quot;&quot; : specifier.type + &quot;&quot;;
  }

  FormatSpecifier.prototype.toString = function() {
    return this.fill
        + this.align
        + this.sign
        + this.symbol
        + (this.zero ? &quot;0&quot; : &quot;&quot;)
        + (this.width === undefined ? &quot;&quot; : Math.max(1, this.width | 0))
        + (this.comma ? &quot;,&quot; : &quot;&quot;)
        + (this.precision === undefined ? &quot;&quot; : &quot;.&quot; + Math.max(0, this.precision | 0))
        + (this.trim ? &quot;~&quot; : &quot;&quot;)
        + this.type;
  };

  // Trims insignificant zeros, e.g., replaces 1.2000k with 1.2k.
  function formatTrim(s) {
    out: for (var n = s.length, i = 1, i0 = -1, i1; i < n; ++i) {
      switch (s[i]) {
        case &quot;.&quot;: i0 = i1 = i; break;
        case &quot;0&quot;: if (i0 === 0) i0 = i; i1 = i; break;
        default: if (!+s[i]) break out; if (i0 > 0) i0 = 0; break;
      }
    }
    return i0 > 0 ? s.slice(0, i0) + s.slice(i1 + 1) : s;
  }

  var prefixExponent;

  function formatPrefixAuto(x, p) {
    var d = formatDecimal(x, p);
    if (!d) return x + &quot;&quot;;
    var coefficient = d[0],
        exponent = d[1],
        i = exponent - (prefixExponent = Math.max(-8, Math.min(8, Math.floor(exponent / 3))) * 3) + 1,
        n = coefficient.length;
    return i === n ? coefficient
        : i > n ? coefficient + new Array(i - n + 1).join(&quot;0&quot;)
        : i > 0 ? coefficient.slice(0, i) + &quot;.&quot; + coefficient.slice(i)
        : &quot;0.&quot; + new Array(1 - i).join(&quot;0&quot;) + formatDecimal(x, Math.max(0, p + i - 1))[0]; // less than 1y!
  }

  function formatRounded(x, p) {
    var d = formatDecimal(x, p);
    if (!d) return x + &quot;&quot;;
    var coefficient = d[0],
        exponent = d[1];
    return exponent < 0 ? &quot;0.&quot; + new Array(-exponent).join(&quot;0&quot;) + coefficient
        : coefficient.length > exponent + 1 ? coefficient.slice(0, exponent + 1) + &quot;.&quot; + coefficient.slice(exponent + 1)
        : coefficient + new Array(exponent - coefficient.length + 2).join(&quot;0&quot;);
  }

  var formatTypes = {
    &quot;%&quot;: function(x, p) { return (x * 100).toFixed(p); },
    &quot;b&quot;: function(x) { return Math.round(x).toString(2); },
    &quot;c&quot;: function(x) { return x + &quot;&quot;; },
    &quot;d&quot;: function(x) { return Math.round(x).toString(10); },
    &quot;e&quot;: function(x, p) { return x.toExponential(p); },
    &quot;f&quot;: function(x, p) { return x.toFixed(p); },
    &quot;g&quot;: function(x, p) { return x.toPrecision(p); },
    &quot;o&quot;: function(x) { return Math.round(x).toString(8); },
    &quot;p&quot;: function(x, p) { return formatRounded(x * 100, p); },
    &quot;r&quot;: formatRounded,
    &quot;s&quot;: formatPrefixAuto,
    &quot;X&quot;: function(x) { return Math.round(x).toString(16).toUpperCase(); },
    &quot;x&quot;: function(x) { return Math.round(x).toString(16); }
  };

  function identity(x) {
    return x;
  }

  var map = Array.prototype.map,
      prefixes = [&quot;y&quot;,&quot;z&quot;,&quot;a&quot;,&quot;f&quot;,&quot;p&quot;,&quot;n&quot;,&quot;µ&quot;,&quot;m&quot;,&quot;&quot;,&quot;k&quot;,&quot;M&quot;,&quot;G&quot;,&quot;T&quot;,&quot;P&quot;,&quot;E&quot;,&quot;Z&quot;,&quot;Y&quot;];

  function formatLocale(locale) {
    var group = locale.grouping === undefined || locale.thousands === undefined ? identity : formatGroup(map.call(locale.grouping, Number), locale.thousands + &quot;&quot;),
        currencyPrefix = locale.currency === undefined ? &quot;&quot; : locale.currency[0] + &quot;&quot;,
        currencySuffix = locale.currency === undefined ? &quot;&quot; : locale.currency[1] + &quot;&quot;,
        decimal = locale.decimal === undefined ? &quot;.&quot; : locale.decimal + &quot;&quot;,
        numerals = locale.numerals === undefined ? identity : formatNumerals(map.call(locale.numerals, String)),
        percent = locale.percent === undefined ? &quot;%&quot; : locale.percent + &quot;&quot;,
        minus = locale.minus === undefined ? &quot;-&quot; : locale.minus + &quot;&quot;,
        nan = locale.nan === undefined ? &quot;NaN&quot; : locale.nan + &quot;&quot;;

    function newFormat(specifier) {
      specifier = formatSpecifier(specifier);

      var fill = specifier.fill,
          align = specifier.align,
          sign = specifier.sign,
          symbol = specifier.symbol,
          zero = specifier.zero,
          width = specifier.width,
          comma = specifier.comma,
          precision = specifier.precision,
          trim = specifier.trim,
          type = specifier.type;

      // The &quot;n&quot; type is an alias for &quot;,g&quot;.
      if (type === &quot;n&quot;) comma = true, type = &quot;g&quot;;

      // The &quot;&quot; type, and any invalid type, is an alias for &quot;.12~g&quot;.
      else if (!formatTypes[type]) precision === undefined && (precision = 12), trim = true, type = &quot;g&quot;;

      // If zero fill is specified, padding goes after sign and before digits.
      if (zero || (fill === &quot;0&quot; && align === &quot;=&quot;)) zero = true, fill = &quot;0&quot;, align = &quot;=&quot;;

      // Compute the prefix and suffix.
      // For SI-prefix, the suffix is lazily computed.
      var prefix = symbol === &quot;$&quot; ? currencyPrefix : symbol === &quot;#&quot; && /[boxX]/.test(type) ? &quot;0&quot; + type.toLowerCase() : &quot;&quot;,
          suffix = symbol === &quot;$&quot; ? currencySuffix : /[%p]/.test(type) ? percent : &quot;&quot;;

      // What format function should we use?
      // Is this an integer type?
      // Can this type generate exponential notation?
      var formatType = formatTypes[type],
          maybeSuffix = /[defgprs%]/.test(type);

      // Set the default precision if not specified,
      // or clamp the specified precision to the supported range.
      // For significant precision, it must be in [1, 21].
      // For fixed precision, it must be in [0, 20].
      precision = precision === undefined ? 6
          : /[gprs]/.test(type) ? Math.max(1, Math.min(21, precision))
          : Math.max(0, Math.min(20, precision));

      function format(value) {
        var valuePrefix = prefix,
            valueSuffix = suffix,
            i, n, c;

        if (type === &quot;c&quot;) {
          valueSuffix = formatType(value) + valueSuffix;
          value = &quot;&quot;;
        } else {
          value = +value;

          // Determine the sign. -0 is not less than 0, but 1 / -0 is!
          var valueNegative = value < 0 || 1 / value < 0;

          // Perform the initial formatting.
          value = isNaN(value) ? nan : formatType(Math.abs(value), precision);

          // Trim insignificant zeros.
          if (trim) value = formatTrim(value);

          // If a negative value rounds to zero after formatting, and no explicit positive sign is requested, hide the sign.
          if (valueNegative && +value === 0 && sign !== &quot;+&quot;) valueNegative = false;

          // Compute the prefix and suffix.
          valuePrefix = (valueNegative ? (sign === &quot;(&quot; ? sign : minus) : sign === &quot;-&quot; || sign === &quot;(&quot; ? &quot;&quot; : sign) + valuePrefix;
          valueSuffix = (type === &quot;s&quot; ? prefixes[8 + prefixExponent / 3] : &quot;&quot;) + valueSuffix + (valueNegative && sign === &quot;(&quot; ? &quot;)&quot; : &quot;&quot;);

          // Break the formatted value into the integer “value” part that can be
          // grouped, and fractional or exponential “suffix” part that is not.
          if (maybeSuffix) {
            i = -1, n = value.length;
            while (++i < n) {
              if (c = value.charCodeAt(i), 48 > c || c > 57) {
                valueSuffix = (c === 46 ? decimal + value.slice(i + 1) : value.slice(i)) + valueSuffix;
                value = value.slice(0, i);
                break;
              }
            }
          }
        }

        // If the fill character is not &quot;0&quot;, grouping is applied before padding.
        if (comma && !zero) value = group(value, Infinity);

        // Compute the padding.
        var length = valuePrefix.length + value.length + valueSuffix.length,
            padding = length < width ? new Array(width - length + 1).join(fill) : &quot;&quot;;

        // If the fill character is &quot;0&quot;, grouping is applied after padding.
        if (comma && zero) value = group(padding + value, padding.length ? width - valueSuffix.length : Infinity), padding = &quot;&quot;;

        // Reconstruct the final output based on the desired alignment.
        switch (align) {
          case &quot;<&quot;: value = valuePrefix + value + valueSuffix + padding; break;
          case &quot;=&quot;: value = valuePrefix + padding + value + valueSuffix; break;
          case &quot;^&quot;: value = padding.slice(0, length = padding.length >> 1) + valuePrefix + value + valueSuffix + padding.slice(length); break;
          default: value = padding + valuePrefix + value + valueSuffix; break;
        }

        return numerals(value);
      }

      format.toString = function() {
        return specifier + &quot;&quot;;
      };

      return format;
    }

    function formatPrefix(specifier, value) {
      var f = newFormat((specifier = formatSpecifier(specifier), specifier.type = &quot;f&quot;, specifier)),
          e = Math.max(-8, Math.min(8, Math.floor(exponent(value) / 3))) * 3,
          k = Math.pow(10, -e),
          prefix = prefixes[8 + e / 3];
      return function(value) {
        return f(k * value) + prefix;
      };
    }

    return {
      format: newFormat,
      formatPrefix: formatPrefix
    };
  }

  var locale;
  var format;
  var formatPrefix;

  defaultLocale({
    decimal: &quot;.&quot;,
    thousands: &quot;,&quot;,
    grouping: [3],
    currency: [&quot;$&quot;, &quot;&quot;],
    minus: &quot;-&quot;
  });

  function defaultLocale(definition) {
    locale = formatLocale(definition);
    format = locale.format;
    formatPrefix = locale.formatPrefix;
    return locale;
  }

  function formatter(value, specifier) {
    const formatFunc = specifier ? format(specifier) : formatValue;

    if (Array.isArray(value)) {
      const [first, second] = value;
      if (first === -Infinity) {
        return `< ${formatFunc(second)}`;
      }
      if (second === Infinity) {
        return `> ${formatFunc(first)}`;
      }
      return `${formatFunc(first)} - ${formatFunc(second)}`;
    }
    return formatFunc(value);
  }

  function formatValue(value) {
    if (typeof value === 'number') {
      return formatNumber(value);
    }
    return value;
  }

  function formatNumber(value) {
    if (!Number.isInteger(value)) {
      return value.toLocaleString(undefined, {
        minimumFractionDigits: 2,
        maximumFractionDigits: 3
      });
    }
    return value.toLocaleString();
  }

  function updateViewport(id, map) {
    function updateMapInfo() {
      const mapInfo$ = document.getElementById(id);
      const center = map.getCenter();
      const lat = center.lat.toFixed(6);
      const lng = center.lng.toFixed(6);
      const zoom = map.getZoom().toFixed(2);

      mapInfo$.innerText = `viewport={'zoom': ${zoom}, 'lat': ${lat}, 'lng': ${lng}}`;
    }

    updateMapInfo();

    map.on('zoom', updateMapInfo);
    map.on('move', updateMapInfo);
  }

  function getBasecolorSettings(basecolor) {
    return {
      'version': 8,
      'sources': {},
      'layers': [{
          'id': 'background',
          'type': 'background',
          'paint': {
              'background-color': basecolor
          }
      }]
    };
  }

  function getImageElement(mapIndex) {
    const id = mapIndex !== undefined ? `map-image-${mapIndex}` : 'map-image';
    return document.getElementById(id);
  }

  function getContainerElement(mapIndex) {
    const id = mapIndex !== undefined ? `main-container-${mapIndex}` : 'main-container';
    return document.getElementById(id);
  }

  function saveImage(mapIndex) {
    const img = getImageElement(mapIndex);
    const container = getContainerElement(mapIndex);

    html2canvas(container)
      .then((canvas) => setMapImage(canvas, img, container));
  }

  function setMapImage(canvas, img, container) {
    const src = canvas.toDataURL();
    img.setAttribute('src', src);
    img.style.display = 'block';
    container.style.display = 'none';
  }

  function resetPopupClick(interactivity) {
    interactivity.off('featureClick');
  }

  function resetPopupHover(interactivity) {
    interactivity.off('featureHover');
  }

  function setPopupsClick(map, clickPopup, hoverPopup, interactivity, attrs) {
    interactivity.on('featureClick', (event) => {
      updatePopup(map, clickPopup, event, attrs);
      hoverPopup.remove();
    });
  }

  function setPopupsHover(map, hoverPopup, interactivity, attrs) {
    interactivity.on('featureHover', (event) => {
      updatePopup(map, hoverPopup, event, attrs);
    });
  }

  function updatePopup(map, popup, event, attrs) {
    if (event.features.length > 0) {
      let popupHTML = '';
      const layerIDs = [];

      for (const feature of event.features) {
        if (layerIDs.includes(feature.layerId)) {
          continue;
        }
        // Track layers to add only one feature per layer
        layerIDs.push(feature.layerId);

        for (const item of attrs) {
          const variable = feature.variables[item.name];
          if (variable) {
            let value = variable.value;
            value = formatter(value, item.format);

            popupHTML = `
            <span class=&quot;popup-name&quot;>${item.title}</span>
            <span class=&quot;popup-value&quot;>${value}</span>
          ` + popupHTML;
          }
        }
      }

      if (popupHTML) {
        popup
            .setLngLat([event.coordinates.lng, event.coordinates.lat])
            .setHTML(`<div class=&quot;popup-content&quot;>${popupHTML}</div>`);

        if (!popup.isOpen()) {
          popup.addTo(map);
        }
      } else {
        popup.remove();
      }
    } else {
      popup.remove();
    }
  }

  function setInteractivity(map, interactiveLayers, interactiveMapLayers) {
    const interactivity = new carto.Interactivity(interactiveMapLayers);

    const clickPopup = new mapboxgl.Popup({
      closeButton: true,
      closeOnClick: false
    });

    const hoverPopup = new mapboxgl.Popup({
      closeButton: false,
      closeOnClick: false
    });

    const { clickAttrs, hoverAttrs } = _setInteractivityAttrs(interactiveLayers);

    resetPopupClick(map);
    resetPopupHover(map);

    if (clickAttrs.length > 0) {
      setPopupsClick(map, clickPopup, hoverPopup, interactivity, clickAttrs);
    }

    if (hoverAttrs.length > 0) {
      setPopupsHover(map, hoverPopup, interactivity, hoverAttrs);
    }
  }

  function _setInteractivityAttrs(interactiveLayers) {
    let clickAttrs = [];
    let hoverAttrs = [];

    interactiveLayers.forEach((interactiveLayer) => {
      interactiveLayer.interactivity.forEach((interactivityDef) => {
        if (interactivityDef.event === 'click') {
          clickAttrs = clickAttrs.concat(interactivityDef.attrs);
        } else if (interactivityDef.event === 'hover') {
          hoverAttrs = hoverAttrs.concat(interactivityDef.attrs);
        }
      });
    });

    return { clickAttrs, hoverAttrs };
  }

  function renderWidget(widget, value) {
    widget.element = widget.element || document.querySelector(`#${widget.id}-value`);

    if (value && widget.element) {
      widget.element.innerText = typeof value === 'number' ? formatter(value, widget.options.format) : value;
    }
  }

  function renderBridge(bridge, widget, mapLayer) {
    widget.element = widget.element || document.querySelector(`#${widget.id}`);

    switch (widget.type) {
      case 'histogram':
        const type = _getWidgetType(mapLayer, widget.value, widget.prop);
        const histogram = type === 'category' ? 'categoricalHistogram' : 'numericalHistogram';
        bridge[histogram](widget.element, widget.value, widget.options);
        break;
      case 'category':
        bridge.category(widget.element, widget.value, widget.options);
        break;
      case 'animation':
        widget.options.propertyName = widget.prop;
        bridge.animationControls(widget.element, widget.value, widget.options);
        break;
      case 'time-series':
        widget.options.propertyName = widget.prop;
        bridge.timeSeries(widget.element, widget.value, widget.options);
        break;
    }
  }

  function bridgeLayerWidgets(map, mapLayer, mapSource, widgets) {
    const bridge = new AsBridge.VL.Bridge({
      carto: carto,
      layer: mapLayer,
      source: mapSource,
      map: map
    });

    widgets
      .filter((widget) => widget.has_bridge)
      .forEach((widget) => renderBridge(bridge, widget, mapLayer));

    bridge.build();
  }

  function _getWidgetType(layer, property, value) {
    return layer.metadata && layer.metadata.properties[value] ?
      layer.metadata.properties[value].type
      : _getWidgetPropertyType(layer, property);
  }

  function _getWidgetPropertyType(layer, property) {
    return layer.metadata && layer.metadata.properties[property] ?
      layer.metadata.properties[property].type
      : null;
  }

  function createLegends(layer, legends, layerIndex, mapIndex=0) {
    if (legends.length) {
      legends.forEach((legend, legendIndex) => _createLegend(layer, legend, layerIndex, legendIndex, mapIndex));
    } else {
      _createLegend(layer, legends, layerIndex, 0, mapIndex);
    }
  }

  function _createLegend(layer, legend, layerIndex, legendIndex, mapIndex=0) {
    const element = document.querySelector(`#layer${layerIndex}_map${mapIndex}_legend${legendIndex}`);

    if (legend.prop) {
      const othersLabel = 'Others';   // TODO: i18n
      const prop = legend.prop;
      const dynamic = legend.dynamic;
      const order = legend.ascending ? 'ASC' : 'DESC';
      const variable = legend.variable;
      const config = { othersLabel, variable, order };
      const formatFunc = (value) => formatter(value, legend.format);
      const options = { format: formatFunc, config, dynamic };

      if (legend.type.startsWith('size-continuous')) {
        config.samples = 4;
      }

      AsBridge.VL.Legends.rampLegend(element, layer, prop, options);
    }
  }

  function SourceFactory() {
    const sourceTypes = { GeoJSON, Query, MVT };

    this.createSource = (layer) => {
      return sourceTypes[layer.type](layer);
    };
  }

  function GeoJSON(layer) {
    const options = JSON.parse(JSON.stringify(layer.options));
    const data = _decodeJSONData(layer.data, layer.encode_data);

    return new carto.source.GeoJSON(data, options);
  }

  function Query(layer) {
    const auth = {
      username: layer.credentials.username,
      apiKey: layer.credentials.api_key || 'default_public'
    };

    const config = {
      serverURL: layer.credentials.base_url || `https://${layer.credentials.username}.carto.com/`
    };

    return new carto.source.SQL(layer.data, auth, config);
  }

  function MVT(layer) {
    return new carto.source.MVT(layer.data.file, JSON.parse(layer.data.metadata));
  }

  function _decodeJSONData(data, encodeData) {
    try {
      if (encodeData) {
        const decodedJSON = pako.inflate(atob(data), { to: 'string' });
        return JSON.parse(decodedJSON);
      } else {
        return JSON.parse(data);
      }
    } catch(error) {
      throw new Error(`
      Error: &quot;${error}&quot;. CARTOframes is not able to parse your local data because it is too large.
      Please, disable the data compresion with encode_data=False in your Layer class.
    `);
    }
  }

  const factory = new SourceFactory();

  function initMapLayer(layer, layerIndex, numLayers, hasLegends, map, mapIndex) {
    const mapSource = factory.createSource(layer);
    const mapViz = new carto.Viz(layer.viz);
    const mapLayer = new carto.Layer(`layer${layerIndex}`, mapSource, mapViz);
    const mapLayerIndex = numLayers - layerIndex - 1;

    try {
      mapLayer._updateLayer.catch(displayError);
    } catch (e) {
      throw e;
    }

    mapLayer.addTo(map);

    setLayerLegend(layer, mapLayerIndex, mapLayer, mapIndex, hasLegends);
    setLayerWidgets(map, layer, mapLayer, mapLayerIndex, mapSource);

    return mapLayer;
  }

  function getInteractiveLayers(layers, mapLayers) {
    const interactiveLayers = [];
    const interactiveMapLayers = [];

    layers.forEach((layer, index) => {
      if (layer.interactivity) {
        interactiveLayers.push(layer);
        interactiveMapLayers.push(mapLayers[index]);
      }
    });

    return { interactiveLayers, interactiveMapLayers };
  }

  function setLayerLegend(layer, mapLayerIndex, mapLayer, mapIndex, hasLegends) {
    if (hasLegends && layer.legends) {
      createLegends(mapLayer, layer.legends, mapLayerIndex, mapIndex);
    }
  }

  function setLayerWidgets(map, layer, mapLayer, mapLayerIndex, mapSource) {
    if (layer.widgets.length) {
      initLayerWidgets(layer.widgets, mapLayerIndex);
      updateLayerWidgets(layer.widgets, mapLayer);
      bridgeLayerWidgets(map, mapLayer, mapSource, layer.widgets);
    }
  }

  function initLayerWidgets(widgets, mapLayerIndex) {
    widgets.forEach((widget, widgetIndex) => {
      const id = `layer${mapLayerIndex}_widget${widgetIndex}`;
      widget.id = id;
    });
  }

  function updateLayerWidgets(widgets, mapLayer) {
    mapLayer.on('updated', () => renderLayerWidgets(widgets, mapLayer));
  }

  function renderLayerWidgets(widgets, mapLayer) {
    const variables = mapLayer.viz.variables;

    widgets
      .filter((widget) => !widget.has_bridge)
      .forEach((widget) => {
        const name = widget.variable_name;
        const value = getWidgetValue(name, variables);
        renderWidget(widget, value);
      });
  }

  function getWidgetValue(name, variables) {
    return name && variables[name] ? variables[name].value : null;
  }

  function setReady(settings) {
    try {
      return settings.maps ? initMaps(settings.maps) : initMap(settings);
    } catch (e) {
      displayError(e);
    }
  }

  function initMaps(maps) {
    return maps.map((mapSettings, mapIndex) => {
      return initMap(mapSettings, mapIndex);
    });
  }

  function initMap(settings, mapIndex) {
    const basecolor = getBasecolorSettings(settings.basecolor);
    const basemapStyle =  BASEMAPS[settings.basemap] || settings.basemap || basecolor;
    const container = mapIndex !== undefined ? `map-${mapIndex}` : 'map';
    const map = createMap(container, basemapStyle, settings.bounds, settings.mapboxtoken);

    if (settings.show_info) {
      const id = mapIndex !== undefined ? `map-info-${mapIndex}` : 'map-info';
      updateViewport(id, map);
    }

    if (settings.camera) {
      map.flyTo(settings.camera);
    }

    return initLayers(map, settings, mapIndex);
  }

  function initLayers(map, settings, mapIndex) {
    const numLayers = settings.layers.length;
    const hasLegends = settings.has_legends;
    const isStatic = settings.is_static;
    const layers = settings.layers;
    const mapLayers = getMapLayers(
      layers,
      numLayers,
      hasLegends,
      map,
      mapIndex
    );

    if (settings.layer_selector) {
      addLayersSelector(layers.reverse(), mapLayers.reverse(), mapIndex);
    }

    setInteractiveLayers(map, layers, mapLayers);

    return waitForMapLayersLoad(isStatic, mapIndex, mapLayers);
  }

  function waitForMapLayersLoad(isStatic, mapIndex, mapLayers) {
    return new Promise((resolve) => {
      carto.on('loaded', mapLayers, onMapLayersLoaded.bind(
        this, isStatic, mapIndex, mapLayers, resolve)
      );
    });
  }

  function onMapLayersLoaded(isStatic, mapIndex, mapLayers, resolve) {
    if (isStatic) {
      saveImage(mapIndex);
    }

    resolve(mapLayers);
  }

  function getMapLayers(layers, numLayers, hasLegends, map, mapIndex) {
    return layers.map((layer, layerIndex) => {
      return initMapLayer(layer, layerIndex, numLayers, hasLegends, map, mapIndex);
    });
  }

  function setInteractiveLayers(map, layers, mapLayers) {
    const { interactiveLayers, interactiveMapLayers } = getInteractiveLayers(layers, mapLayers);

    if (interactiveLayers && interactiveLayers.length > 0) {
      setInteractivity(map, interactiveLayers, interactiveMapLayers);
    }
  }

  function addLayersSelector(layers, mapLayers, mapIndex) {
    const layerSelectorId = mapIndex !== undefined ? `#layer-selector-${mapIndex}` : '#layer-selector';
    const layerSelector$ = document.querySelector(layerSelectorId);
    const layersInfo = mapLayers.map((layer, index) => {
      return {
        title: layers[index].title || `Layer ${index}`,
        id: layer.id,
        checked: true
      };
    });

    const layerSelector = new AsBridge.VL.Layers(layerSelector$, carto, layersInfo, mapLayers);

    layerSelector.build();
  }

  function createMap(container, basemapStyle, bounds, accessToken) {
    const map = createMapboxGLMap(container, basemapStyle, accessToken);

    map.addControl(attributionControl);
    map.fitBounds(bounds, FIT_BOUNDS_SETTINGS);

    return map;
  }

  function createMapboxGLMap(container, style, accessToken) {
    if (accessToken) {
      mapboxgl.accessToken = accessToken;
    }

    return new mapboxgl.Map({
      container,
      style,
      zoom: 9,
      dragRotate: false,
      attributionControl: false
    });
  }

  function init(settings) {
    setReady(settings);
  }

  return init;

}());
</script>
<script>
  document
  .querySelector('as-responsive-content')
  .addEventListener('ready', () => {
    const basecolor = '';
    const basemap = 'Positron';
    const bounds = [[-122.51899999999999, 47.1559], [-121.315, 47.7776]];
    const camera = null;
    const has_legends = 'true' === 'true';
    const is_static = 'None' === 'true';
    const layer_selector = 'False' === 'true';
    const mapboxtoken = '';
    const show_info = 'None' === 'true';

    init({
      basecolor,
      basemap,
      bounds,
      camera,
      has_legends,
      is_static,
      layer_selector,
      layers,
      mapboxtoken,
      show_info
    });
});
</script>
</html>
">

</iframe>



# Computation of W matrix

https://pysal.org/packages/

## Creation of a W matrix for regular grid data
To start, consider the case of a regular square lattice grid of dimension (e. g.) 5-by-5.


```python
from libpysal.weights import lat2W

w = lat2W(5, 5)
print(w)
```

    <libpysal.weights.weights.W object at 0x7fda233d9350>



```python
w.n
```




    25




```python
w.neighbors
```




    {0: [5, 1],
     1: [0, 6, 2],
     2: [1, 7, 3],
     3: [2, 8, 4],
     4: [3, 9],
     5: [0, 10, 6],
     6: [1, 5, 11, 7],
     7: [2, 6, 12, 8],
     8: [3, 7, 13, 9],
     9: [4, 8, 14],
     10: [5, 15, 11],
     11: [6, 10, 16, 12],
     12: [7, 11, 17, 13],
     13: [8, 12, 18, 14],
     14: [9, 13, 19],
     15: [10, 20, 16],
     16: [11, 15, 21, 17],
     17: [12, 16, 22, 18],
     18: [13, 17, 23, 19],
     19: [14, 18, 24],
     20: [15, 21],
     21: [16, 20, 22],
     22: [17, 21, 23],
     23: [18, 22, 24],
     24: [19, 23]}




```python
w_card = pd.Series(w.cardinalities)
w_card.head()
```




    0    2
    1    3
    2    3
    3    3
    4    2
    dtype: int64




```python
import seaborn as sns
sns.displot(w_card, bins=3);
```


![png](seai_lab2_files/seai_lab2_51_0.png)


## Creation of a W matrix for irregular data
In the case of irregular data, it is possible to import a GAL (.gal).


```python
#gal = libpysal.io.open(libpysal.examples.get_path('name_of_gal_file.gal'),'r')
#w = gal.read()
#gal.close()
```

## Creation of W matrix from a GeoPandas GeoDataFrame


```python
from libpysal.weights import Queen, Rook

columbus = gpd.read_file("columbus/columbus.shp")
columbus = columbus.to_crs(4326)
w_queen = Queen.from_dataframe(columbus)
```


```python
w_queen.n
```




    49




```python
w_queen.neighbors
```




    {0: [1, 2],
     1: [0, 2, 3],
     2: [0, 1, 3, 4],
     3: [1, 2, 4, 7],
     4: [2, 3, 5, 7, 8, 10, 14, 15],
     5: [8, 4],
     6: [11, 12, 13, 7],
     7: [3, 4, 6, 10, 11, 12],
     8: [4, 5, 9, 14, 19, 21, 24, 25],
     9: [16, 8, 19, 21],
     10: [4, 7, 11, 14, 15],
     11: [6, 7, 10, 12, 13, 15],
     12: [11, 13, 6, 7],
     13: [17, 18, 6, 11, 12, 15],
     14: [4, 8, 24, 10, 25, 15],
     15: [4, 10, 11, 13, 14, 17, 23, 24],
     16: [9, 19, 22],
     17: [18, 15, 13, 23],
     18: [17, 13, 23],
     19: [32, 34, 39, 8, 9, 16, 21, 22, 26, 31],
     20: [33, 29, 23],
     21: [19, 8, 9, 26, 27, 25],
     22: [16, 19, 31],
     23: [17, 18, 20, 24, 28, 29, 15],
     24: [8, 14, 15, 23, 25, 27, 28, 29],
     25: [21, 8, 24, 27, 28, 14],
     26: [32, 27, 19, 21],
     27: [32, 34, 36, 37, 21, 24, 25, 26, 28],
     28: [36, 37, 23, 24, 25, 27, 29],
     29: [20, 36, 23, 24, 28],
     30: [33, 35, 38],
     31: [40, 19, 22, 39],
     32: [26, 27, 34, 19],
     33: [41, 35, 20, 30],
     34: [32, 19, 37, 39, 27, 42, 43],
     35: [33, 38, 41, 45, 30],
     36: [37, 42, 27, 28, 29, 44],
     37: [34, 36, 43, 42, 27, 28],
     38: [35, 45, 30],
     39: [34, 19, 40, 46, 31],
     40: [31, 46, 39],
     41: [33, 35],
     42: [34, 36, 37, 43, 44, 47],
     43: [48, 34, 37, 42, 47],
     44: [48, 42, 36, 47],
     45: [35, 38],
     46: [40, 39],
     47: [48, 42, 43, 44],
     48: [43, 44, 47]}




```python
w_queen[0]
```




    {1: 1.0, 2: 1.0}




```python
w_queen[0][1]
```




    1.0




```python
w_queen.mean_neighbors
```




    4.816326530612245




```python
w_queen.min_neighbors
```




    2




```python
w_queen.max_neighbors
```




    10




```python
w_queen.islands
```




    []




```python
w_card = pd.Series(w_queen.cardinalities)
sns.displot(w_card, bins=10);
```


![png](seai_lab2_files/seai_lab2_64_0.png)



```python
from splot.libpysal import plot_spatial_weights
plot_spatial_weights(w_queen, columbus);
```

    /usr/local/lib/python3.7/dist-packages/splot/_viz_libpysal_mpl.py:115: UserWarning: Geometry is in a geographic CRS. Results from 'centroid' are likely incorrect. Use 'GeoSeries.to_crs()' to re-project geometries to a projected CRS before this operation.
    
      centroids_shp = gdf.centroid.values
    /usr/local/lib/python3.7/dist-packages/splot/_viz_libpysal_mpl.py:154: UserWarning: Geometry is in a geographic CRS. Results from 'centroid' are likely incorrect. Use 'GeoSeries.to_crs()' to re-project geometries to a projected CRS before this operation.
    
      gdf.centroid.plot(ax=ax, **node_kws)



![png](seai_lab2_files/seai_lab2_65_1.png)



```python
w_rook = Rook.from_dataframe(columbus)
plot_spatial_weights(w_rook, columbus);
```

    /usr/local/lib/python3.7/dist-packages/splot/_viz_libpysal_mpl.py:115: UserWarning: Geometry is in a geographic CRS. Results from 'centroid' are likely incorrect. Use 'GeoSeries.to_crs()' to re-project geometries to a projected CRS before this operation.
    
      centroids_shp = gdf.centroid.values
    /usr/local/lib/python3.7/dist-packages/splot/_viz_libpysal_mpl.py:154: UserWarning: Geometry is in a geographic CRS. Results from 'centroid' are likely incorrect. Use 'GeoSeries.to_crs()' to re-project geometries to a projected CRS before this operation.
    
      gdf.centroid.plot(ax=ax, **node_kws)



![png](seai_lab2_files/seai_lab2_66_1.png)



```python
w_queen.pct_nonzero
```




    9.82923781757601




```python
w_rook.pct_nonzero
```




    8.329862557267806



## W Matrix for point data


```python
boston = gpd.read_file("boston/boston.shp")
boston.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>TOWN</th>
      <th>TOWNNO</th>
      <th>TRACT</th>
      <th>LON</th>
      <th>LAT</th>
      <th>x</th>
      <th>y</th>
      <th>MEDV</th>
      <th>CMEDV</th>
      <th>CRIM</th>
      <th>ZN</th>
      <th>INDUS</th>
      <th>CHAS</th>
      <th>NOX</th>
      <th>RM</th>
      <th>AGE</th>
      <th>DIS</th>
      <th>RAD</th>
      <th>TAX</th>
      <th>PTRATIO</th>
      <th>B</th>
      <th>LSTAT</th>
      <th>geometry</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2011.0</td>
      <td>-70.955</td>
      <td>42.2550</td>
      <td>338.73</td>
      <td>4679.73</td>
      <td>24.0</td>
      <td>24.0</td>
      <td>0.00632</td>
      <td>18.0</td>
      <td>2.31</td>
      <td>0.0</td>
      <td>0.538</td>
      <td>6.575</td>
      <td>65.2</td>
      <td>4.0900</td>
      <td>1.0</td>
      <td>296.0</td>
      <td>15.3</td>
      <td>396.90</td>
      <td>4.98</td>
      <td>POINT (338.730 4679.730)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>2021.0</td>
      <td>-70.950</td>
      <td>42.2875</td>
      <td>339.23</td>
      <td>4683.33</td>
      <td>21.6</td>
      <td>21.6</td>
      <td>0.02731</td>
      <td>0.0</td>
      <td>7.07</td>
      <td>0.0</td>
      <td>0.469</td>
      <td>6.421</td>
      <td>78.9</td>
      <td>4.9671</td>
      <td>2.0</td>
      <td>242.0</td>
      <td>17.8</td>
      <td>396.90</td>
      <td>9.14</td>
      <td>POINT (339.230 4683.330)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>2022.0</td>
      <td>-70.936</td>
      <td>42.2830</td>
      <td>340.37</td>
      <td>4682.80</td>
      <td>34.7</td>
      <td>34.7</td>
      <td>0.02729</td>
      <td>0.0</td>
      <td>7.07</td>
      <td>0.0</td>
      <td>0.469</td>
      <td>7.185</td>
      <td>61.1</td>
      <td>4.9671</td>
      <td>2.0</td>
      <td>242.0</td>
      <td>17.8</td>
      <td>392.83</td>
      <td>4.03</td>
      <td>POINT (340.370 4682.800)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>2031.0</td>
      <td>-70.928</td>
      <td>42.2930</td>
      <td>341.05</td>
      <td>4683.89</td>
      <td>33.4</td>
      <td>33.4</td>
      <td>0.03237</td>
      <td>0.0</td>
      <td>2.18</td>
      <td>0.0</td>
      <td>0.458</td>
      <td>6.998</td>
      <td>45.8</td>
      <td>6.0622</td>
      <td>3.0</td>
      <td>222.0</td>
      <td>18.7</td>
      <td>394.63</td>
      <td>2.94</td>
      <td>POINT (341.050 4683.890)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>2032.0</td>
      <td>-70.922</td>
      <td>42.2980</td>
      <td>341.56</td>
      <td>4684.44</td>
      <td>36.2</td>
      <td>36.2</td>
      <td>0.06905</td>
      <td>0.0</td>
      <td>2.18</td>
      <td>0.0</td>
      <td>0.458</td>
      <td>7.147</td>
      <td>54.2</td>
      <td>6.0622</td>
      <td>3.0</td>
      <td>222.0</td>
      <td>18.7</td>
      <td>396.90</td>
      <td>5.33</td>
      <td>POINT (341.560 4684.440)</td>
    </tr>
  </tbody>
</table>
</div>




```python
boston.plot(column="MEDV", figsize=(10, 6), scheme='Quantiles', k=7, cmap='Blues',legend=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7fda229a4cd0>




![png](seai_lab2_files/seai_lab2_71_1.png)


### KNN
Creates nearest neighbor weights matrix based on k nearest neighbors.


```python
from libpysal.weights import KNN

knn5 = KNN.from_dataframe(boston, k=5)
knn5
```




    <libpysal.weights.distance.KNN at 0x7fda22ffb590>




```python
knn5.n
```




    506




```python
knn5.mean_neighbors
```




    5.0




```python
knn5.neighbors
```




    {0: [31, 29, 34, 32, 28],
     1: [26, 27, 28, 29, 25],
     2: [1, 3, 29, 6, 28],
     3: [4, 6, 2, 5, 1],
     4: [3, 5, 6, 8, 7],
     5: [4, 3, 8, 9, 6],
     6: [3, 4, 7, 2, 1],
     7: [8, 10, 11, 9, 12],
     8: [7, 10, 9, 11, 5],
     9: [10, 8, 7, 11, 61],
     10: [8, 9, 7, 11, 61],
     11: [10, 49, 48, 7, 8],
     12: [47, 46, 7, 48, 11],
     13: [26, 14, 25, 15, 27],
     14: [17, 24, 25, 13, 15],
     15: [14, 16, 17, 13, 24],
     16: [15, 45, 17, 14, 18],
     17: [14, 21, 22, 23, 24],
     18: [19, 21, 20, 37, 17],
     19: [20, 21, 18, 33, 22],
     20: [33, 19, 21, 22, 34],
     21: [22, 20, 17, 33, 19],
     22: [23, 33, 21, 32, 20],
     23: [32, 22, 24, 30, 33],
     24: [30, 23, 25, 32, 14],
     25: [27, 26, 24, 30, 28],
     26: [25, 27, 13, 1, 28],
     27: [28, 25, 26, 30, 31],
     28: [27, 29, 31, 25, 26],
     29: [28, 27, 1, 31, 26],
     30: [24, 31, 23, 32, 25],
     31: [30, 32, 28, 24, 27],
     32: [23, 30, 22, 24, 33],
     33: [20, 22, 34, 21, 32],
     34: [33, 32, 20, 22, 23],
     35: [36, 19, 18, 20, 33],
     36: [35, 37, 18, 19, 38],
     37: [18, 38, 36, 19, 35],
     38: [37, 89, 87, 36, 90],
     39: [42, 40, 86, 41, 84],
     40: [39, 84, 86, 42, 83],
     41: [42, 53, 40, 43, 39],
     42: [41, 39, 43, 40, 53],
     43: [44, 45, 51, 48, 46],
     44: [48, 47, 46, 43, 45],
     45: [46, 44, 47, 15, 16],
     46: [45, 47, 44, 12, 48],
     47: [48, 12, 46, 49, 44],
     48: [47, 49, 11, 44, 12],
     49: [48, 11, 47, 44, 50],
     50: [59, 51, 52, 49, 58],
     51: [52, 50, 53, 59, 43],
     52: [51, 50, 58, 53, 59],
     53: [51, 52, 43, 41, 50],
     54: [65, 41, 53, 55, 66],
     55: [56, 57, 52, 58, 53],
     56: [57, 55, 58, 52, 60],
     57: [56, 55, 58, 52, 60],
     58: [60, 59, 52, 50, 62],
     59: [50, 61, 60, 62, 58],
     60: [62, 59, 61, 58, 50],
     61: [62, 59, 60, 9, 10],
     62: [61, 60, 63, 59, 9],
     63: [62, 60, 61, 58, 59],
     64: [63, 62, 60, 61, 57],
     65: [66, 40, 82, 83, 41],
     66: [65, 67, 82, 68, 83],
     67: [68, 69, 82, 66, 81],
     68: [69, 67, 70, 66, 82],
     69: [68, 70, 67, 72, 71],
     70: [72, 69, 71, 73, 79],
     71: [74, 73, 79, 75, 78],
     72: [70, 73, 71, 193, 74],
     73: [74, 71, 72, 192, 75],
     74: [75, 73, 71, 78, 76],
     75: [74, 76, 78, 96, 71],
     76: [96, 75, 78, 97, 95],
     77: [95, 76, 78, 94, 93],
     78: [79, 75, 76, 77, 71],
     79: [78, 71, 80, 75, 77],
     80: [81, 83, 93, 85, 79],
     81: [80, 83, 82, 79, 93],
     82: [81, 83, 80, 67, 65],
     83: [81, 82, 80, 84, 85],
     84: [86, 85, 83, 93, 80],
     85: [84, 93, 86, 87, 80],
     86: [84, 85, 39, 87, 40],
     87: [88, 89, 92, 85, 38],
     88: [89, 91, 92, 87, 90],
     89: [88, 90, 91, 87, 38],
     90: [89, 91, 117, 88, 116],
     91: [88, 89, 90, 111, 116],
     92: [94, 88, 87, 91, 89],
     93: [85, 94, 77, 80, 92],
     94: [92, 93, 77, 95, 88],
     95: [96, 99, 97, 77, 76],
     96: [95, 97, 76, 99, 98],
     97: [96, 98, 99, 95, 76],
     98: [97, 175, 96, 99, 76],
     99: [97, 95, 96, 98, 175],
     100: [109, 104, 103, 108, 110],
     101: [133, 174, 173, 103, 172],
     102: [103, 174, 101, 133, 173],
     103: [102, 133, 174, 101, 104],
     104: [105, 103, 100, 106, 133],
     105: [106, 130, 129, 104, 132],
     106: [105, 107, 129, 130, 104],
     107: [108, 106, 112, 109, 105],
     108: [107, 109, 112, 106, 100],
     109: [100, 108, 110, 112, 107],
     110: [111, 109, 112, 100, 108],
     111: [113, 110, 112, 116, 115],
     112: [108, 113, 114, 107, 111],
     113: [111, 116, 115, 112, 114],
     114: [122, 115, 121, 113, 112],
     115: [114, 121, 118, 116, 113],
     116: [117, 113, 118, 115, 111],
     117: [118, 116, 119, 115, 90],
     118: [117, 116, 115, 119, 121],
     119: [117, 118, 495, 494, 116],
     120: [492, 125, 121, 124, 494],
     121: [115, 124, 120, 492, 122],
     122: [123, 114, 124, 121, 492],
     123: [122, 124, 126, 492, 114],
     124: [492, 125, 123, 122, 121],
     125: [492, 124, 120, 490, 126],
     126: [123, 124, 492, 125, 490],
     127: [128, 140, 139, 380, 137],
     128: [127, 137, 129, 139, 140],
     129: [137, 136, 130, 128, 105],
     130: [105, 132, 131, 129, 135],
     131: [132, 134, 171, 135, 130],
     132: [131, 134, 171, 130, 135],
     133: [101, 174, 103, 173, 134],
     134: [131, 132, 171, 135, 133],
     135: [169, 168, 131, 171, 132],
     136: [137, 129, 168, 157, 130],
     137: [136, 129, 128, 138, 139],
     138: [150, 139, 158, 137, 157],
     139: [140, 141, 138, 128, 137],
     140: [139, 127, 380, 141, 128],
     141: [148, 143, 139, 147, 149],
     142: [144, 143, 145, 147, 141],
     143: [144, 147, 142, 148, 141],
     144: [143, 145, 142, 147, 148],
     145: [144, 147, 152, 146, 143],
     146: [149, 151, 147, 150, 148],
     147: [148, 149, 143, 146, 145],
     148: [149, 147, 141, 146, 143],
     149: [148, 147, 146, 150, 151],
     150: [159, 149, 151, 146, 158],
     151: [146, 159, 150, 156, 149],
     152: [146, 151, 145, 153, 154],
     153: [154, 155, 152, 156, 151],
     154: [153, 155, 156, 151, 152],
     155: [154, 153, 156, 160, 152],
     156: [159, 160, 151, 154, 158],
     157: [161, 158, 136, 138, 168],
     158: [159, 150, 160, 157, 156],
     159: [150, 156, 158, 151, 160],
     160: [156, 158, 159, 151, 154],
     161: [157, 166, 162, 168, 158],
     162: [163, 161, 166, 165, 160],
     163: [162, 165, 166, 161, 164],
     164: [181, 218, 182, 163, 165],
     165: [166, 163, 162, 167, 161],
     166: [161, 168, 165, 169, 162],
     167: [170, 165, 169, 171, 172],
     168: [135, 169, 166, 136, 161],
     169: [135, 170, 168, 171, 166],
     170: [171, 169, 135, 167, 134],
     171: [170, 134, 131, 132, 169],
     172: [173, 101, 171, 174, 170],
     173: [174, 101, 172, 133, 102],
     174: [173, 101, 133, 102, 103],
     175: [178, 177, 102, 98, 174],
     176: [177, 187, 186, 175, 178],
     177: [176, 178, 186, 175, 179],
     178: [179, 177, 173, 172, 174],
     179: [180, 178, 186, 172, 177],
     180: [182, 179, 181, 183, 167],
     181: [182, 164, 180, 218, 183],
     182: [181, 183, 180, 217, 164],
     183: [184, 182, 217, 180, 181],
     184: [183, 185, 216, 217, 182],
     185: [184, 214, 215, 183, 186],
     186: [177, 179, 185, 176, 178],
     187: [176, 177, 190, 188, 186],
     188: [189, 205, 187, 213, 190],
     189: [188, 191, 192, 190, 187],
     190: [192, 187, 176, 98, 189],
     191: [192, 189, 190, 188, 193],
     192: [191, 190, 189, 73, 74],
     193: [194, 72, 73, 191, 192],
     194: [193, 72, 191, 73, 192],
     195: [203, 196, 205, 189, 188],
     196: [197, 198, 195, 199, 203],
     197: [196, 198, 199, 195, 203],
     198: [196, 197, 195, 194, 199],
     199: [200, 197, 202, 196, 203],
     200: [199, 251, 252, 250, 202],
     201: [238, 239, 250, 242, 204],
     202: [204, 203, 201, 251, 238],
     203: [202, 195, 204, 199, 206],
     204: [202, 201, 238, 239, 281],
     205: [188, 213, 206, 207, 214],
     206: [207, 208, 213, 209, 211],
     207: [206, 208, 209, 211, 210],
     208: [207, 209, 210, 206, 211],
     209: [211, 210, 208, 207, 212],
     210: [209, 235, 211, 208, 236],
     211: [209, 212, 210, 235, 234],
     212: [211, 215, 209, 210, 234],
     213: [214, 206, 212, 205, 207],
     214: [185, 215, 213, 212, 184],
     215: [212, 214, 216, 185, 184],
     216: [223, 221, 215, 184, 217],
     217: [219, 182, 183, 181, 184],
     218: [164, 181, 182, 363, 217],
     219: [217, 220, 216, 358, 218],
     220: [219, 224, 358, 221, 223],
     221: [223, 222, 216, 234, 220],
     222: [221, 234, 223, 235, 220],
     223: [221, 216, 222, 234, 220],
     224: [220, 358, 226, 225, 227],
     225: [360, 224, 359, 227, 268],
     226: [227, 224, 233, 231, 222],
     227: [226, 231, 228, 225, 224],
     228: [229, 227, 480, 225, 230],
     229: [228, 230, 231, 227, 480],
     230: [231, 278, 232, 229, 227],
     231: [230, 232, 227, 226, 233],
     232: [231, 279, 230, 233, 237],
     233: [226, 234, 232, 235, 237],
     234: [235, 222, 221, 211, 223],
     235: [234, 210, 211, 236, 209],
     236: [210, 237, 235, 208, 209],
     237: [236, 232, 233, 235, 279],
     238: [239, 201, 242, 281, 204],
     239: [238, 281, 201, 242, 204],
     240: [241, 282, 242, 281, 239],
     241: [240, 242, 243, 256, 244],
     242: [243, 238, 241, 239, 201],
     243: [242, 247, 244, 249, 241],
     244: [247, 245, 243, 246, 248],
     245: [246, 244, 247, 248, 255],
     246: [245, 248, 247, 253, 244],
     247: [244, 248, 246, 243, 245],
     248: [249, 247, 246, 245, 244],
     249: [248, 250, 247, 243, 251],
     250: [251, 249, 201, 242, 243],
     251: [250, 249, 201, 252, 248],
     252: [249, 251, 248, 253, 250],
     253: [246, 254, 248, 245, 252],
     254: [253, 255, 246, 245, 248],
     255: [245, 254, 246, 244, 253],
     256: [241, 244, 240, 243, 245],
     257: [258, 264, 421, 365, 259],
     258: [259, 257, 264, 362, 260],
     259: [258, 362, 260, 261, 264],
     260: [261, 362, 259, 262, 258],
     261: [260, 262, 263, 259, 264],
     262: [261, 260, 360, 263, 267],
     263: [266, 265, 261, 264, 422],
     264: [265, 421, 258, 257, 263],
     265: [264, 266, 422, 421, 263],
     266: [263, 265, 422, 479, 264],
     267: [262, 263, 266, 261, 360],
     268: [359, 360, 357, 361, 358],
     269: [483, 272, 484, 482, 273],
     270: [271, 272, 485, 484, 269],
     271: [270, 272, 292, 303, 485],
     272: [270, 269, 271, 292, 273],
     273: [269, 272, 291, 483, 274],
     274: [275, 276, 277, 278, 229],
     275: [274, 278, 277, 276, 230],
     276: [274, 275, 277, 278, 273],
     277: [275, 278, 276, 279, 274],
     278: [275, 279, 230, 277, 232],
     279: [232, 278, 230, 280, 277],
     280: [279, 281, 282, 277, 237],
     281: [282, 239, 280, 238, 240],
     282: [281, 280, 240, 277, 239],
     283: [240, 282, 276, 291, 277],
     284: [289, 285, 290, 295, 283],
     285: [284, 286, 289, 256, 287],
     286: [285, 287, 289, 284, 288],
     287: [288, 289, 298, 297, 300],
     288: [297, 296, 289, 287, 295],
     289: [288, 287, 284, 296, 297],
     290: [295, 296, 294, 291, 292],
     291: [273, 290, 292, 294, 276],
     292: [271, 294, 272, 270, 303],
     293: [297, 294, 296, 295, 303],
     294: [295, 292, 296, 293, 290],
     295: [296, 290, 294, 297, 293],
     296: [295, 297, 294, 293, 290],
     297: [296, 293, 288, 295, 294],
     298: [300, 299, 287, 288, 297],
     299: [300, 298, 301, 287, 288],
     300: [298, 299, 301, 288, 297],
     301: [302, 293, 300, 303, 297],
     302: [301, 329, 303, 330, 328],
     303: [271, 292, 293, 270, 294],
     304: [305, 306, 307, 464, 319],
     305: [487, 304, 306, 486, 465],
     306: [464, 465, 459, 458, 463],
     307: [309, 319, 308, 463, 306],
     308: [318, 319, 309, 313, 314],
     309: [308, 307, 312, 319, 313],
     310: [311, 312, 462, 452, 461],
     311: [310, 312, 313, 462, 452],
     312: [309, 313, 310, 308, 462],
     313: [308, 312, 309, 314, 318],
     314: [318, 313, 316, 308, 317],
     315: [316, 340, 314, 339, 323],
     316: [314, 315, 323, 322, 317],
     317: [318, 321, 314, 322, 316],
     318: [308, 319, 314, 317, 313],
     319: [308, 318, 307, 309, 313],
     320: [327, 321, 326, 317, 324],
     321: [322, 320, 324, 317, 323],
     322: [323, 321, 324, 316, 317],
     323: [322, 336, 321, 316, 324],
     324: [321, 336, 322, 326, 323],
     325: [326, 327, 333, 332, 330],
     326: [327, 325, 324, 320, 321],
     327: [320, 326, 321, 328, 324],
     328: [329, 330, 327, 326, 320],
     329: [328, 302, 330, 327, 320],
     330: [328, 331, 325, 329, 332],
     331: [332, 330, 325, 333, 328],
     332: [331, 333, 325, 330, 334],
     333: [334, 332, 325, 335, 326],
     334: [333, 335, 346, 332, 337],
     335: [336, 337, 334, 333, 324],
     336: [324, 323, 337, 338, 322],
     337: [338, 336, 335, 339, 323],
     338: [339, 337, 340, 336, 323],
     339: [340, 338, 323, 316, 315],
     340: [339, 338, 315, 316, 323],
     341: [342, 349, 343, 344, 348],
     342: [343, 341, 340, 344, 339],
     343: [342, 340, 338, 339, 344],
     344: [337, 348, 343, 338, 335],
     345: [346, 347, 334, 348, 333],
     346: [345, 347, 334, 333, 348],
     347: [345, 346, 348, 334, 333],
     348: [347, 344, 346, 334, 345],
     349: [350, 341, 342, 351, 348],
     350: [349, 351, 341, 352, 354],
     351: [352, 353, 354, 350, 355],
     352: [353, 351, 354, 355, 350],
     353: [354, 352, 355, 351, 350],
     354: [353, 355, 351, 352, 347],
     355: [354, 353, 352, 351, 347],
     356: [363, 361, 163, 162, 218],
     357: [358, 268, 359, 361, 363],
     358: [357, 359, 268, 220, 224],
     359: [268, 360, 357, 361, 358],
     360: [359, 268, 262, 361, 260],
     361: [362, 363, 268, 359, 357],
     362: [259, 260, 361, 258, 261],
     363: [356, 361, 357, 362, 218],
     364: [365, 366, 153, 367, 257],
     365: [364, 366, 257, 367, 421],
     366: [367, 411, 365, 417, 412],
     367: [411, 366, 410, 368, 409],
     368: [369, 410, 367, 407, 409],
     369: [368, 367, 410, 370, 407],
     370: [371, 372, 407, 369, 368],
     371: [370, 372, 406, 374, 369],
     372: [406, 371, 374, 370, 373],
     373: [374, 406, 375, 372, 376],
     374: [373, 406, 372, 375, 371],
     375: [378, 377, 376, 373, 379],
     376: [375, 377, 378, 379, 373],
     377: [379, 378, 375, 376, 381],
     378: [377, 375, 379, 381, 376],
     379: [381, 377, 378, 375, 376],
     380: [381, 140, 379, 378, 377],
     381: [379, 377, 380, 378, 375],
     382: [383, 387, 388, 389, 489],
     383: [382, 388, 387, 389, 386],
     384: [386, 385, 387, 383, 388],
     385: [386, 384, 392, 387, 388],
     386: [384, 385, 387, 392, 388],
     387: [388, 386, 383, 384, 385],
     388: [387, 383, 389, 386, 384],
     389: [388, 383, 382, 387, 390],
     390: [389, 391, 488, 388, 383],
     391: [390, 503, 500, 491, 499],
     392: [385, 386, 387, 384, 388],
     393: [394, 395, 397, 396, 398],
     394: [395, 393, 396, 397, 402],
     395: [394, 396, 397, 393, 402],
     396: [395, 402, 397, 401, 394],
     397: [396, 395, 401, 394, 402],
     398: [397, 405, 401, 393, 399],
     399: [400, 405, 401, 404, 402],
     400: [404, 401, 399, 402, 403],
     401: [400, 402, 399, 404, 396],
     402: [403, 401, 396, 400, 404],
     403: [404, 402, 400, 401, 439],
     404: [400, 403, 399, 402, 401],
     405: [399, 401, 400, 404, 397],
     406: [372, 374, 373, 371, 375],
     407: [410, 409, 408, 368, 370],
     408: [409, 410, 412, 413, 411],
     409: [408, 410, 411, 412, 407],
     410: [409, 407, 408, 368, 411],
     411: [412, 409, 367, 410, 408],
     412: [413, 411, 417, 408, 409],
     413: [412, 417, 408, 414, 411],
     414: [413, 415, 416, 438, 412],
     415: [438, 416, 437, 429, 414],
     416: [415, 438, 428, 418, 417],
     417: [418, 412, 413, 411, 416],
     418: [417, 427, 416, 425, 419],
     419: [420, 425, 418, 427, 421],
     420: [419, 421, 425, 422, 423],
     421: [420, 265, 264, 422, 419],
     422: [479, 265, 423, 420, 266],
     423: [424, 425, 479, 422, 420],
     424: [478, 426, 423, 430, 476],
     425: [427, 419, 426, 423, 420],
     426: [478, 427, 428, 477, 424],
     427: [428, 425, 426, 418, 477],
     428: [477, 427, 426, 429, 478],
     429: [437, 477, 428, 436, 438],
     430: [476, 478, 475, 431, 477],
     431: [475, 432, 430, 435, 436],
     432: [475, 431, 474, 434, 430],
     433: [450, 434, 455, 432, 474],
     434: [435, 433, 450, 449, 432],
     435: [436, 434, 449, 445, 431],
     436: [445, 437, 435, 429, 431],
     437: [438, 436, 444, 429, 445],
     438: [415, 437, 444, 429, 416],
     439: [444, 440, 443, 403, 442],
     440: [442, 439, 443, 403, 444],
     441: [447, 446, 442, 443, 448],
     442: [443, 440, 441, 446, 439],
     443: [446, 442, 444, 445, 439],
     444: [437, 439, 445, 438, 443],
     445: [436, 437, 444, 446, 443],
     446: [443, 447, 445, 449, 441],
     447: [441, 448, 446, 449, 443],
     448: [451, 447, 449, 450, 446],
     449: [435, 448, 434, 446, 450],
     450: [433, 434, 451, 449, 454],
     451: [448, 453, 450, 454, 452],
     452: [461, 453, 451, 448, 447],
     453: [451, 454, 461, 460, 452],
     454: [453, 450, 455, 451, 460],
     455: [433, 454, 456, 450, 474],
     456: [457, 455, 458, 466, 454],
     457: [466, 458, 456, 465, 459],
     458: [457, 459, 460, 464, 456],
     459: [458, 460, 464, 463, 457],
     460: [459, 454, 453, 458, 461],
     461: [453, 452, 462, 460, 451],
     462: [463, 461, 459, 460, 452],
     463: [462, 459, 461, 460, 464],
     464: [306, 459, 458, 465, 463],
     465: [466, 457, 458, 464, 487],
     466: [457, 465, 456, 458, 464],
     467: [469, 473, 474, 468, 455],
     468: [470, 469, 487, 471, 467],
     469: [468, 470, 467, 471, 472],
     470: [468, 469, 471, 487, 472],
     471: [472, 482, 470, 468, 481],
     472: [471, 481, 470, 482, 469],
     473: [467, 479, 472, 469, 267],
     474: [432, 433, 476, 475, 434],
     475: [431, 432, 430, 435, 476],
     476: [430, 478, 475, 432, 431],
     477: [428, 478, 426, 429, 430],
     478: [477, 426, 430, 424, 476],
     479: [422, 423, 266, 265, 420],
     480: [481, 482, 228, 472, 483],
     481: [480, 482, 472, 471, 483],
     482: [471, 481, 483, 472, 480],
     483: [269, 482, 481, 480, 471],
     484: [486, 485, 269, 487, 270],
     485: [484, 486, 270, 305, 487],
     486: [484, 487, 485, 305, 468],
     487: [486, 468, 465, 470, 305],
     488: [489, 491, 490, 389, 382],
     489: [488, 490, 382, 383, 491],
     490: [489, 488, 125, 491, 126],
     491: [488, 490, 489, 493, 125],
     492: [124, 125, 120, 123, 126],
     493: [494, 498, 491, 495, 120],
     494: [493, 495, 498, 496, 120],
     495: [494, 496, 119, 493, 498],
     496: [497, 495, 498, 494, 499],
     497: [496, 499, 498, 500, 495],
     498: [499, 493, 494, 496, 497],
     499: [498, 500, 497, 496, 391],
     500: [499, 501, 391, 502, 497],
     501: [502, 504, 500, 503, 505],
     502: [503, 504, 501, 505, 500],
     503: [502, 504, 501, 391, 505],
     504: [502, 505, 503, 501, 500],
     505: [504, 502, 503, 501, 500]}




```python
plot_spatial_weights(knn5, boston);
```


![png](seai_lab2_files/seai_lab2_77_0.png)


### Kernel Weights
Spatial weights based on kernel functions.

For **fixed bandwidth**, 
$$h_{i}=\max (d k n n) \forall i$$ where $d k n n$ is a vector of k-nearest neighbor distances (the distance to the kth nearest neighbor for each observation). 

For adaptive bandwidths, $$h_{i}=d k n n_{i}$$


**Kernel function defined as follows with:**
$$
z_{i, j}=d_{i, j} / h_{i}
$$
triangular
$$
K(z)=(1-|z|) i f|z| \leq 1
$$
uniform
$$
K(z)=1 / 2 \text { if }|z| \leq 1
$$
quadratic
$$
K(z)=(3 / 4)\left(1-z^{2}\right) i f|z| \leq 1
$$
quartic
$$
K(z)=(15 / 16)\left(1-z^{2}\right)^{2} i f|z| \leq 1
$$
gaussian
$$
K(z)=(2 \pi)^{(-1 / 2)} \exp \left(-z^{2} / 2\right)
$$

https://pysal.org/libpysal/generated/libpysal.weights.Kernel.html


```python
from libpysal.weights import distance
w_kernel = distance.Kernel.from_dataframe(boston)
```


```python
w_kernel.function
```




    'triangular'




```python
w_kernel.bandwidth[0:10]
```




    array([[5.27056976],
           [5.27056976],
           [5.27056976],
           [5.27056976],
           [5.27056976],
           [5.27056976],
           [5.27056976],
           [5.27056976],
           [5.27056976],
           [5.27056976]])




```python
w_kernel.weights[0]
```




    [0.163551559050497,
     0.19181618325114325,
     0.09473389104628172,
     0.13092225033037153,
     0.07496742804829448,
     0.08191080022181252,
     0.1261552782976385,
     0.19097921738634083,
     0.1720602864115155,
     0.3010077516629547,
     0.10995087934229786,
     0.31958894493655776,
     0.2733728853634749,
     0.36773125208680824,
     0.27811466105273197,
     1.0,
     0.35814762302133973,
     0.4164829256867967,
     0.497978319440454,
     0.5124309808630476,
     0.5261957306180548,
     0.4742346749992036,
     0.2285687077374301,
     0.29823222830546314,
     0.17614003438822645,
     0.309349123035617,
     0.4617704592448053,
     0.2733134374315873,
     0.42287221770873373,
     0.27605558105763905,
     0.396646687116729,
     0.38536818952869667,
     0.20741404543113307,
     0.11238701394849415,
     0.37411750639295605,
     0.4722016578165268,
     0.32215713806517166,
     0.41625162522416426,
     0.31040541399739163,
     0.33961806947625883,
     0.06727845568338509,
     0.09626616719351899]




```python
plot_spatial_weights(w_kernel, boston);
```


![png](seai_lab2_files/seai_lab2_83_0.png)



```python
w_kernel_gaussian = distance.Kernel.from_dataframe(boston, function="gaussian", fixed=False, k=20)
```


```python
w_kernel_gaussian.weights[0]
```




    [0.3989422804014327,
     0.31705773159802025,
     0.3127930500228602,
     0.3082482854503523,
     0.30064563932915683,
     0.29998736630684864,
     0.2965929724745923,
     0.2837127108292177,
     0.28156780010707066,
     0.2814900153816355,
     0.27486510267232905,
     0.2710281274575302,
     0.2671846662070748,
     0.2649967458134385,
     0.2617059886370584,
     0.25532273799876404,
     0.2492897977719749,
     0.24840149007380918,
     0.24522374826057816,
     0.2448581503743604,
     0.2419707487162134]




```python
plot_spatial_weights(w_kernel_gaussian, boston);
```


![png](seai_lab2_files/seai_lab2_86_0.png)


### Distance


```python
w_distance15 = distance.DistanceBand.from_dataframe(boston, 1.5, binary=True)
```

    /usr/local/lib/python3.7/dist-packages/libpysal/weights/weights.py:172: UserWarning: The weights matrix is not fully connected: 
     There are 64 disconnected components.
     There are 49 islands with ids: 0, 40, 54, 55, 64, 65, 66, 67, 195, 196, 197, 198, 199, 200, 202, 203, 204, 252, 253, 254, 255, 256, 273, 283, 284, 285, 286, 287, 289, 291, 299, 301, 302, 303, 330, 335, 341, 342, 343, 344, 347, 348, 349, 350, 351, 352, 353, 354, 355.
      warnings.warn(message)



```python
w_distance15.pct_nonzero
```




    2.596509865800122




```python
w_distance15.islands
```




    [0,
     40,
     54,
     55,
     64,
     65,
     66,
     67,
     195,
     196,
     197,
     198,
     199,
     200,
     202,
     203,
     204,
     252,
     253,
     254,
     255,
     256,
     273,
     283,
     284,
     285,
     286,
     287,
     289,
     291,
     299,
     301,
     302,
     303,
     330,
     335,
     341,
     342,
     343,
     344,
     347,
     348,
     349,
     350,
     351,
     352,
     353,
     354,
     355]




```python
plot_spatial_weights(w_distance15, boston);
```


![png](seai_lab2_files/seai_lab2_91_0.png)



```python
w_distance5 = distance.DistanceBand.from_dataframe(boston, 5, binary=True)
```


```python
w_distance5.pct_nonzero
```




    20.07139620990798




```python
plot_spatial_weights(w_distance5, boston);
```


![png](seai_lab2_files/seai_lab2_94_0.png)


# Kriging

https://geostat-framework.readthedocs.io/projects/pykrige/en/stable/contents.html#


```python
! pip3 install pykrige
```

    Collecting pykrige
    [?25l  Downloading https://files.pythonhosted.org/packages/b5/bc/f4123cd138a515f325fe1c02f4ccd508503aea1d06f10cec379a0c27e725/PyKrige-1.6.0-cp37-cp37m-manylinux2010_x86_64.whl (957kB)
    [K     |████████████████████████████████| 962kB 7.9MB/s 
    [?25hRequirement already satisfied: scipy>=1.1.0 in /usr/local/lib/python3.7/dist-packages (from pykrige) (1.4.1)
    Requirement already satisfied: numpy>=1.14.5 in /usr/local/lib/python3.7/dist-packages (from pykrige) (1.19.5)
    Installing collected packages: pykrige
    Successfully installed pykrige-1.6.0



```python
import numpy as np
import pykrige.kriging_tools as kt
from pykrige.ok import OrdinaryKriging
import matplotlib.pyplot as plt


data = np.array(
    [
        [0.3, 1.2, 0.47],
        [1.9, 0.6, 0.56],
        [1.1, 3.2, 0.74],
        [3.3, 4.4, 1.47],
        [4.7, 3.8, 1.74],
    ]
)

gridx = np.arange(0.0, 5.5, 0.5)
gridy = np.arange(0.0, 5.5, 0.5)
```


```python
OK = OrdinaryKriging(
    data[:, 0],
    data[:, 1],
    data[:, 2],
    variogram_model="linear",
    verbose=True,
    enable_plotting=True,
    enable_statistics = True
)

```

    Plotting Enabled
    
    Adjusting data for anisotropy...
    Initializing variogram model...
    Coordinates type: 'euclidean' 
    
    Using 'linear' Variogram Model
    Slope: 0.11914486053372102
    Nugget: 1.562799151461731e-10 
    



![png](seai_lab2_files/seai_lab2_98_1.png)


    Calculating statistics on variogram model fit...
    Q1 = 0.7185997466464226
    Q2 = 0.5261655056850497
    cR = 0.22836851705603034 
    



```python
z, ss = OK.execute("grid", gridx, gridy)
```

    Executing Ordinary Kriging...
    



```python
OK.display_variogram_model()
```


![png](seai_lab2_files/seai_lab2_100_0.png)



```python
OK.get_epsilon_residuals()
```




    array([0.11939362, 0.31524397, 1.13335687, 0.99419705])




```python
OK.plot_epsilon_residuals()
```


![png](seai_lab2_files/seai_lab2_102_0.png)



```python
OK.print_statistics()
```

    Q1 = 0.8540638346446238
    Q2 = 0.7955197182710158
    cR = 0.4108295341866522



```python
plt.imshow(z)
```




    <matplotlib.image.AxesImage at 0x7fda222f59d0>




![png](seai_lab2_files/seai_lab2_104_1.png)



```python
ss
```




    masked_array(
      data=[[0.25923484621514353, 0.21697173215927953, 0.18562005009310606,
             0.15070036160851258, 0.1409807977110183, 0.19349623439414743,
             0.27091057749162145, 0.34859396413807986, 0.4218274091144686,
             0.4914972861602811, 0.5599388590592126],
            [0.1685790750642299, 0.13433839128069075, 0.12282338387603808,
             0.07928152497428621, 0.033412197372541405, 0.13348943280667194,
             0.22452086202401816, 0.3032191203296969, 0.37293023486324334,
             0.43771179023565937, 0.5016155100223009],
            [0.08513321025062208, 0.057344001806422594, 0.0988201151086116,
             0.09207956894947228, 0.0831828752132979, 0.14137090557413895,
             0.21305277711097992, 0.2779203059340609, 0.3357999549087324,
             0.3905481098685688, 0.44686986881283053],
            [0.09191464967628578, 0.07010101583643995, 0.11140934135535302,
             0.12986229606731423, 0.14347812569342044, 0.17561920857304442,
             0.21951485895469935, 0.2632407706365101, 0.3039890173487808,
             0.34502695685402585, 0.3918395827580563],
            [0.14948214785440378, 0.1217475985806349, 0.12854881481594435,
             0.14615953270233276, 0.16830020601219053, 0.19453240208520173,
             0.22194674394560182, 0.24688656697346245, 0.26945761171205823,
             0.295046175074278, 0.3320008321431087],
            [0.18356850506947925, 0.13375394095649235, 0.11179043555732382,
             0.1292000992277427, 0.1638315723909173, 0.1922874069134982,
             0.21092004612934748, 0.22122630209830302, 0.22624840776159327,
             0.23505804793713853, 0.26320910634511757],
            [0.20473710925155325, 0.12341468403522206, 0.047664586806003544,
             0.0878067281803101, 0.14560488298636257, 0.1756929458350838,
             0.18605280230202975, 0.18464159922712753, 0.1733635576216061,
             0.161427003572866, 0.18313405454162326],
            [0.23880816509066907, 0.14857123026131117, 0.07168774750225619,
             0.09555229371525809, 0.13971346731080803, 0.15425752100036777,
             0.14803555190518472, 0.13852577609948494, 0.11991632336379174,
             0.07613074414793403, 0.09809025883238591],
            [0.29627771686047677, 0.21928741671751967, 0.16671941780353483,
             0.154640117045358, 0.1555778354210307, 0.13660241671581147,
             0.09487459548352549, 0.08099406302375851, 0.0913473847441243,
             0.05590106420059135, 0.08496678734127737],
            [0.36864012548353403, 0.301222610214792, 0.2514557631550581,
             0.21967591573605158, 0.1908443620848134, 0.1446775191834751,
             0.06874055530188111, 0.04813430003152433, 0.10761668023856749,
             0.12913542357871338, 0.16666691988014123],
            [0.4479163263002224, 0.38482474342694295, 0.3333107579320962,
             0.29083217969923514, 0.2490868172716495, 0.20002319469798968,
             0.1504203103061949, 0.1406596133305867, 0.1738847320860175,
             0.2104606566988974, 0.25584260269013936]],
      mask=[[False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False],
            [False, False, False, False, False, False, False, False, False,
             False, False]],
      fill_value=1e+20)



https://geostat-framework.readthedocs.io/projects/pykrige/en/stable/variogram_models.html


```python

```