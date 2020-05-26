1) make faceforesics submission file (done)

blazeface cannot detect some benchmark images 

2) extract face from benchmark images and compare performances among following 4 methods:
- mtcnn (done)
- blazeface (done)
- blazeface + mtcnn (backup)
- mtcnn + blazeface(backup) (no meaning)

compare points are effect and time. (done)

3) complete albumentations
4) find model list and compare 

# Conclusion:
- Blazeface is better than MTCNN, but it still cannot detect some faces and misjudge some faces. This incur miss-sample in test datasets. How and when to solve this?
- FaceForensices submission failed due to their system failure. I wrote letter to ask but no response.