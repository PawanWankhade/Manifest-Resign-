# Manifest-Resign-
ClickOnce manifest signing can be a little confusing for someone going through the process the very first time. This is probably because it involves signing multiple files in a particular sequence. Once you understand the process conceptually it becomes fairly easy to follow. In this post, I hope to provide a quick summary of the important things you need to know about manifests and this signing/resigning business..

This are some steps:

1. First of all remove all the .deploy extensions of the files that are the part of the deployment.
  (if file extension is .dll)
  >ren *.dll.deploy *.
2. Make sure that .deploy extension removed from all deployable files.(config,exe)
3. sign the Application Manifest : Application Files – the exe and dlls associated with the application.
  > mage –update Myapplication.exe.manifest –certfile mycert.pfx 
4. Again add removed .deploy extension to all the deployable files.
 >ren *.dll *.dll.deploy
5. Now sign the deployment manifest 
  > mage.exe –update Myapplication.application –appmanifest “Application Files\MyApplication_%Version%\Myapplication.exe.manifest” –certfile mycert.pfx 
6. Done...!  
