
## Prerequisites

- Setup k3s


## Steps

1. Clone this repository

2. Download yolo.h5 into webcam/ from:

https://github.com/OlafenwaMoses/ImageAI/releases/download/1.0/yolo.h5

3. Build docker
```
$ cd webcam
$ docker build -t kojiha/webcam .
$ docker push kojiha/webcam
```
* Replace docker tag with yours.


4. Deploy the pod
```
$ k3s kubectl apply -f webcam.yaml
```

5. See results
```
$ k3s kubectl logs -f webcam
```
