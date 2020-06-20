# annotated-transformer issue with the jupyter notebook. 

Using this version of pytorch: 

-conda install pytorch torchvision cudatoolkit=10.2 -c pytorch 

-You might have to install additional things such as seaborn and etc but thats included in the first few lines of the jupyter notebook. 

-There are also small files that have to be download via uncommenting wget but that should be okay!
 
The issue seems to be that there is a storing of data from previous training epochs as it goes along and trains. Over time, the data takes up all the storage on my gpus resulting in the stopping of the algo. I suspect it might be something in the MultiGPULossCompute component that is storing the data as we go along OR in the  


"Training the System

#!wget https://s3.amazonaws.com/opennmt-models/iwslt.pt

if False:
    model_opt = NoamOpt(model.src_embed[0].d_model, 1, 2000,
            torch.optim.Adam(model.parameters(), lr=0, betas=(0.9, 0.98), eps=1e-9))
    for epoch in range(10): 
........" 


You will see that I have actually been able to train the translation model a bit before i run out of memory on my gpus. 


I've looked all around the web and couldn't find where to change the code. I've done most of the hard yards getting the code to run in the sections beforehand, just.. this section is the one im having trouble with. 


Original source: 
http://nlp.seas.harvard.edu/2018/04/03/attention.html 
The original source actually doesn't even 
