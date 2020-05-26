
# Code

```
from blazeface import BlazeFace

net = BlazeFace().to(device)
net.load_weights("blazeface.pth")
net.load_anchors("anchors.npy")

# Optionally change the thresholds:
net.min_score_thresh = 0.75
net.min_suppression_threshold = 0.3



# wrap up
def read_faces(img_path, detector):
    # read img
    img = cv2.cvtColor(cv2.imread(img_path), cv2.COLOR_BGR2RGB)
    img = fill_resize(img)
    
    # detect face
    detections = net.predict_on_image(img)
    faces = get_faces(img, detections)
    
    result = []
    for f in faces:
        f = cv2.resize(f, (224, 224))
        result.append(f)
    
    return result
    
    
    
start = time.time()

for path in tqdm(imgs):
    
    faces = read_faces(path, net)
    for i, f in enumerate(faces):
        cv2.imwrite(os.path.join('../faces_blaze', path[-8:-4]+'_'+str(i)+'.png'), cv2.cvtColor(f, cv2.COLOR_RGB2BGR))
        
end = time.time()
print(end-start)

```

# Performance

|Error Rate | Time | Not Detected Rate |
|:--:|:--:|:--:|
|5/1017 | 32 | 30/1000 |