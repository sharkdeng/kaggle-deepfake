# Code

```
from mtcnn import MTCNN

img = cv2.cvtColor(cv2.imread(imgs[7]), cv2.COLOR_BGR2RGB)
detector = MTCNN()
faces = detector.detect_faces(img)
print(faces)
fig, ax = plt.subplots(1, len(faces), figsize=(6, 6))

for i, f in enumerate(faces):
    xmin = max(int(f['box'][0] - 0.2*f['box'][2]), 0)
    ymin = max(int(f['box'][1] - 0.2*f['box'][3]), 0)
    xmax = min(int(f['box'][0] + f['box'][2] + 0.2*f['box'][2]), img.shape[0])
    ymax = min(int(f['box'][1] + f['box'][3] + 0.2*f['box'][3]), img.shape[0])
    if len(faces) == 1:  
        ax.imshow(img[ymin:ymax, xmin:xmax, :])
    else:
        ax[i].imshow(img[ymin:ymax, xmin:xmax, :])
        
        
        
def get_faces_mtcnn(img_path, margin=0.2):
    
    # get raw faces
    img = cv2.cvtColor(cv2.imread(img_path), cv2.COLOR_BGR2RGB)
    detector = MTCNN()
    faces = detector.detect_faces(img)

    for i, f in enumerate(faces):
        xmin = max(int(f['box'][0] - margin*f['box'][2]), 0)
        ymin = max(int(f['box'][1] - margin*f['box'][3]), 0)
        xmax = min(int(f['box'][0] + f['box'][2] + margin*f['box'][2]), img.shape[0])
        ymax = min(int(f['box'][1] + f['box'][3] + margin*f['box'][3]), img.shape[0])
        r = img[ymin:ymax, xmin:xmax, :]
        
        # fill_resize
        r = fill_resize(r, n_size=(224, 224))
        
        print(os.path.join('../faces_mtcnn', img_path[-8:-4]+'_'+str(i)+'.png'))
        
        # save
        a = cv2.imwrite(os.path.join('../faces_mtcnn', img_path[-8:-4]+'_'+str(i)+'.png'), cv2.cvtColor(r, cv2.COLOR_RGB2BGR))
        
        

start = time.time()
for path in imgs:
    get_faces_mtcnn(path)
end = time.time()
print(end-start)

```




| Error rate | Time | Not Detect|
|:--:|:--:|:--:|
|227/1221=18.6%|1335s| 73|