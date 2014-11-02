clear all;clc;close all;

clc;clear all;close all
%cd D:\picture
%x=dir *O*.jpg
%cd ('E:\phd\Brian')
filename='C:\Documents and Settings\AMR\Desktop\lpr\';
x = dir(fullfile('C:\Documents and Settings\AMR\Desktop\lpr\*.bmp'));

 for i=1:length(x)
    
    zz(:,:,i)=imresize(rgb2gray(imread(strcat(filename,x(i).name))),[128 128]);
    
 end
   for i=1:54

%%%%%%%%feature extraction using dwt2 (discrete wavelet transform)
 [cA1(:,:,i),cH1(:,:,i),cV1(:,:,i),cD1(:,:,i)]=dwt2(zz(:,:,i),'db4');

%%%%%%%%%%%%%%%%%%%%%%%%%%%%pca (principal component analysis)
[a1,b1,xx(:,i)]=princomp([cH1(:,:,i) cV1(:,:,i) cD1(:,:,i)]);

   end

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
p=xx;%neural network input
%neural network target
t=[1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 0 ];
 
net=newfit(p,t,100 );%you can use newfit or newff
%properties of neural network
net.trainparam.epochs=100;%Number of repeats to improve result
net.trainparam.goal=0.001;%The accuracy needed
net.divideParam.trainRatio = 70/100;  % train ratio 70%
net.divideParam.valRatio = 15/100;  % validation ration 15%
net.divideParam.testRatio = 15/100;  % test ratio 15%
 
% learn the network using theprevious properties.
[net]=train(net,p,t);
 
%to test the network with any input and get the output at z
 
z=sim(net,p);
 
 
save net1.mat net

