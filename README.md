# CVinW Readings [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/Computer-Vision-in-the-Wild/CVinW_Readings)

``[Computer Vision in the Wild (CVinW)](https://computer-vision-in-the-wild.github.io/eccv-2022/)'' is an emerging field. This writeup provides a quick introduction of CVinW and maintains a collection of papers on the topic. If you find some missing papers or resourses, please open issues or pull requests (recommended).


# Table of Contents

- [What is Computer Vision in the Wild (CVinW)?](#what-is-computer-vision-in-the-wild)
  - [Goals of CVinW](#star-goals-of-cvinw)
  - [Task Transfer Scenarios are Broad](#one-task-transfer-scenarios-are-broad) 
  - [Task Transfer Cost is Low](#two-task-transfer-cost-is-low )
  - [Benchmarks](#cinema-benchmarks)
- [Papers on Task-level Transfer with Pre-trained Models](#fire-papers-on-task-level-transfer-with-pre-trained-models)
  - [Image Classification in the Wild](#orange_book-image-classification-in-the-wild)
  - [Object Detection in the Wild](#orange_book-object-detection-in-the-wild)
  - [Segmentation in the Wild](#orange_book-segmentation-in-the-wild)
  - [Video Classification in the Wild](#orange_book-video-classification-in-the-wild)
  - [Others](#orange_book-other-visual-recognition-in-the-wild)
- [Papers on Efficient Model Adaptation](#snowflake-papers-on-efficient-model-adaptation)  
  - [Parameter-Efficient Methods](#blue_book-parameter-efficient-methods)
- [Acknowledgements](#beers-acknowledgements)


# What is Computer Vision in the Wild?

### :star: Goals of CVinW
Developing a transferable foundation model/system that can *effortlessly* adapt to *a large range of visual tasks* in the wild. It comes with two key factors: (i) The task transfer scenarios are broad, and (ii) The task transfer cost is low. The main idea is illustrated as follows, please see the detailed description in [ELEVATER paper](https://arxiv.org/abs/2204.08790). 

### :one: Task Transfer Scenarios are Broad

We illustrate and compare CVinW with other settings using a 2D chart in Figure 1, where the space is constructed with two orthogonal dimensions:
input image distribution and output concept set. The 2D chart is divided into four quadrants, based on how the model evaluation stage is different from model development stage. For any visual recognition problems at different granularity such as image classification, object detection and segmentation, the modeling setup cann be categorized into one of the four settings. We see an emerging trend on moving towards CVinW. Interested in the various pre-trained vision models that move towards CVinW? please check out Section :fire:[``Papers on Task-level Transfer with Pre-trained Models''](#fire-papers-on-task-level-transfer-with-pre-trained-models).

<table>
<tr>
  <td  width="50%">
<ul>
  <li><b>The Close-Set Setting. </b> Both training and evaluation distributions are consistent in both dimensions, a typical setting in ML/CV textbooks.</li>
  <li><b>Open-Set/Vocabulary/World Setting.</b> It allows new concepts in evaluation, while typically remains the same visual domain. Please see examples in <a href='https://arxiv.org/abs/1707.00600'>image classification</a>  and <a href='https://arxiv.org/abs/2011.10678'>object detection</a>. </li>
  <li><b>Domain Generalization Setting.</b> Domain shift allows new visual domain in evaluation, while typically remains the same concept pool. Please see examples such as <a href='https://arxiv.org/abs/2007.01434'>DomainBed</a>  and <a href='http://ai.bu.edu/M3SDA/'>DomainNet</a>.  </li>
  <li style="background-color:powderblue;"><b>Computer Vision in the Wild Setting. </b> CVinW allows the flexibility in both dimensions, where any new tasks/datasets in the wild essentially fall into.</li>
</ul>    

</td>
<td>
    <img src="images/fig_cvinw.png" style="width:100%;"> 
</td>
</tr> 
<tr>
  <th> A brief definition with a four-quadrant chart </th>
  <th>Figure 1: The comparison of CVinW with other existing settings</th>
</tr>
</table>


### :two: Task Transfer Cost is Low

One major advantage of pre-trained models is the promise that they can transfer to downstream tasks *effortlessly*. The model adaptation cost is considered in two orthogonal dimensions: *sample-efficiency* and *parameter-efficiency*, as illustrated in Figure 2.  The bottom-left corner and  top-right corner is the most inexpensive and  expensive adaptation strategy, respectively. One may interpolate and  make combinations in the 2D space, to get different model adaptation methods with different cost. To efficient adapt large vision models of the gradaully increaseing size, we see an emerging need on efficient model adaptation. Interested in contributing your smart efficient adaptation algorithms and see how it differs from existing papers? please check out Section :snowflake:[``Papers on Efficient Model Adaptation''](#snowflake-papers-on-efficient-model-adaptation)  .

<table>
<tr>
  <td  width="50%">
<ul>
  <li><b>Sample-efficiency: Zero-, Few-, and Full-shot. </b> Due to the high cost of annotating data, it is often desired to provide a small number of labeled image-label pairs in downstream datasets. Transferable models should be able to reach high performance in this data-limited scenario..</li>
  <li><b>Parameter-efficiency: Frozen Model Inference, Prompting Tuning, Linear Probing vs Full Model Fine-tuning..</b> A smaller number of trainable parameter in model adaptation typically means a small training cost in a new task. </li>
</ul>    

</td>
<td>
    <img src="images/fig_adapation_cost.png" style="width:100%;">
</td>
</tr> 
<tr>
  <th> A breakdown definition of efficient model adaptation</th>
  <th>Figure 2: The 2D chart of model adaptation cost.</th>
</tr>
</table>

 
###  :cinema: Benchmarks

<p>
<font size=3><b>ELEVATER: A Benchmark and Toolkit for Evaluating Language-Augmented Visual Models.</b></font>
<br>
<font size=2>Chunyuan Li*, Haotian Liu*, Liunian Harold Li, Pengchuan Zhang, Jyoti Aneja, Jianwei Yang, Ping Jin, Yong Jae Lee, Houdong Hu, Zicheng Liu, Jianfeng Gao.</font>
<br>
<font size=2> NeurIPS 2022 (Datasets and Benchmarks Track).</font>
<a href='https://arxiv.org/abs/2204.08790'>[paper]</a> <a href='https://computer-vision-in-the-wild.github.io/ELEVATER/'>[benchmark]</a>    
</p>


# :fire: Papers on Task-level Transfer with Pre-trained Models

## :orange_book: Image Classification in the Wild

<p>
<font size=3><b>[CLIP] Learning Transferable Visual Models From Natural Language Supervision.</b></font>
<br>
<font size=2>Alec Radford, Jong Wook Kim, Chris Hallacy, Aditya Ramesh, Gabriel Goh, Sandhini Agarwal, Girish Sastry, Amanda Askell, Pamela Mishkin, Jack Clark, Gretchen Krueger, Ilya Sutskever.</font>
<br>
<font size=2>ICML 2021.</font>
<a href='https://arxiv.org/abs/2103.00020'>[paper]</a> <a href='https://github.com/OpenAI/CLIP'>[code]</a>    
</p>

<p>
<font size=3><b>[ALIGN] Scaling Up Visual and Vision-Language Representation Learning With Noisy Text Supervision.</b></font>
<br>
<font size=2>Chao Jia, Yinfei Yang, Ye Xia, Yi-Ting Chen, Zarana Parekh, Hieu Pham, Quoc V. Le, Yunhsuan Sung, Zhen Li, Tom Duerig.</font>
<br>
<font size=2>ICML 2021.</font>
<a href='https://arxiv.org/abs/2102.05918'>[paper]</a> 
</p>

<p>
<font size=3><b>OpenCLIP.</b></font>
<br>
<font size=2>Gabriel Ilharco*, Mitchell Wortsman*, Nicholas Carlini, Rohan Taori, Achal Dave, Vaishaal Shankar, John Miller, Hongseok Namkoong, Hannaneh Hajishirzi, Ali Farhadi, Ludwig Schmidt.</font>
<br>
<font size=2>10.5281/zenodo.5143773, 2021.</font>
<a href='https://github.com/mlfoundations/open_clip'>[code]</a>   
</p>

<p>
<font size=3><b>Florence: A New Foundation Model for Computer Vision.</b></font>
<br>
<font size=2>Lu Yuan, Dongdong Chen, Yi-Ling Chen, Noel Codella, Xiyang Dai, Jianfeng Gao, Houdong Hu, Xuedong Huang, Boxin Li, Chunyuan Li, Ce Liu, Mengchen Liu, Zicheng Liu, Yumao Lu, Yu Shi, Lijuan Wang, Jianfeng Wang, Bin Xiao, Zhen Xiao, Jianwei Yang, Michael Zeng, Luowei Zhou, Pengchuan Zhang.</font>
<br>
<font size=2>	arXiv:2111.11432, 2022.</font>
<a href='https://arxiv.org/abs/2111.11432'>[paper]</a>
</p>


<p>
<font size=3><b>[UniCL] Unified Contrastive Learning in Image-Text-Label Space.</b></font>
<br>
<font size=2>Jianwei Yang*, Chunyuan Li*, Pengchuan Zhang*, Bin Xiao*, Ce Liu, Lu Yuan, Jianfeng Gao.</font>
<br>
<font size=2>CVPR 2022.</font>
<a href='https://arxiv.org/abs/2204.03610'>[paper]</a>  <a href='https://github.com/microsoft/UniCL'>[code]</a>   
</p>

<p>
<font size=3><b>LiT: Zero-Shot Transfer with Locked-image text Tuning.</b></font>
<br>
<font size=2>Xiaohua Zhai, Xiao Wang, Basil Mustafa, Andreas Steiner, Daniel Keysers, Alexander Kolesnikov, Lucas Beyer.</font>
<br>
<font size=2>CVPR 2022.</font>
<a href='https://arxiv.org/abs/2111.07991'>[paper]</a>
</p>

<p>
<font size=3><b>[DeCLIP] Supervision Exists Everywhere: A Data Efficient Contrastive Language-Image Pre-training Paradigm.</b></font>
<br>
<font size=2>Yangguang Li, Feng Liang, Lichen Zhao, Yufeng Cui, Wanli Ouyang, Jing Shao, Fengwei Yu, Junjie Yan.</font>
<br>
<font size=2>ICLR 2022.</font>
<a href='https://arxiv.org/abs/2110.05208'>[paper]</a>  <a href='https://github.com/Sense-GVT/DeCLIP'>[code]</a>   
</p>

<p>
<font size=3><b>FILIP: Fine-grained Interactive Language-Image Pre-Training.</b></font>
<br>
<font size=2>Lewei Yao, Runhui Huang, Lu Hou, Guansong Lu, Minzhe Niu, Hang Xu, Xiaodan Liang, Zhenguo Li, Xin Jiang, Chunjing Xu.</font>
<br>
<font size=2>ICLR 2022.</font>
<a href='https://arxiv.org/abs/2111.07783'>[paper]</a> 
</p>

<p>
<font size=3><b>SLIP: Self-supervision meets Language-Image Pre-training.</b></font>
<br>
<font size=2>Norman Mu, Alexander Kirillov, David Wagner, Saining Xie.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2112.12750'>[paper]</a>  <a href='https://github.com/facebookresearch/SLIP'>[code]</a>   
</p>

<p>
<font size=3><b>[MS-CLIP]: Learning Visual Representation from Modality-Shared Contrastive Language-Image Pre-training.</b></font>
<br>
<font size=2>Haoxuan You*, Luowei Zhou*, Bin Xiao*, Noel Codella*, Yu Cheng, Ruochen Xu, Shih-Fu Chang, Lu Yuan.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2207.12661'>[paper]</a>  <a href='https://github.com/Hxyou/MSCLIP'>[code]</a>   
</p>


<p>
<font size=3><b>MultiMAE: Multi-modal Multi-task Masked Autoencoders.</b></font>
<br>
<font size=2>Roman Bachmann, David Mizrahi, Andrei Atanov, Amir Zamir.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2204.01678'>[paper]</a>  <a href='https://github.com/EPFL-VILAB/MultiMAE'>[code]</a>  <a href='https://multimae.epfl.ch/'>[project]</a>
</p>

<p>
<font size=3><b>[M3AE] Multimodal Masked Autoencoders Learn Transferable Representations.</b></font>
<br>
<font size=2>Xinyang Geng, Hao Liu, Lisa Lee, Dale Schuurmans, Sergey Levine, Pieter Abbeel.</font>
<br>
<font size=2>	arXiv:2205.14204, 2022.</font>
<a href='https://arxiv.org/abs/2205.14204'>[paper]</a>  <a href='https://github.com/young-geng/m3ae_public'>[code]</a>
</p>



<p>
<font size=3><b>CyCLIP: Cyclic Contrastive Language-Image Pretraining.</b></font>
<br>
<font size=2>Shashank Goel, Hritik Bansal, Sumit Bhatia, Ryan A. Rossi, Vishwa Vinay, Aditya Grover.</font>
<br>
<font size=2>NeurIPS 2022.</font>
<a href='https://arxiv.org/abs/2205.14459'>[paper]</a>  <a href='https://github.com/goel-shashank/CyCLIP'>[code]</a>   
</p>

<p>
<font size=3><b>PyramidCLIP: Hierarchical Feature Alignment for Vision-language Model Pretraining.</b></font>
<br>
<font size=2>Yuting Gao, Jinfeng Liu, Zihan Xu, Jun Zhang, Ke Li, Rongrong Ji, Chunhua Shen.</font>
<br>
<font size=2>NeurIPS 2022.</font>
<a href='https://arxiv.org/abs/2204.14095'>[paper]</a> 
</p>

<p>
<font size=3><b>K-LITE: Learning Transferable Visual Models with External Knowledge.</b></font>
<br>
<font size=2>Sheng Shen*, Chunyuan Li*, Xiaowei Hu*, Yujia Xie, Jianwei Yang, Pengchuan Zhang, Anna Rohrbach, Zhe Gan, Lijuan Wang, Lu Yuan, Ce Liu, Kurt Keutzer, Trevor Darrell, Jianfeng Gao.</font>
<br>
<font size=2>NeurIPS 2022.</font>
<a href='https://arxiv.org/abs/2204.09222'>[paper]</a> 
</p>


<p>
<font size=3><b>UniCLIP: Unified Framework for Contrastive Language-Image Pre-training.</b></font>
<br>
<font size=2>Janghyeon Lee, Jongsuk Kim, Hyounguk Shon, Bumsoo Kim, Seung Hwan Kim, Honglak Lee, Junmo Kim.</font>
<br>
<font size=2>NeurIPS 2022.</font>
<a href='https://arxiv.org/abs/2209.13430'>[paper]</a> 
</p>

<p>
<font size=3><b>CoCa: Contrastive Captioners are Image-Text Foundation Models.</b></font>
<br>
<font size=2>Jiahui Yu, Zirui Wang, Vijay Vasudevan, Legg Yeung, Mojtaba Seyedhosseini, Yonghui Wu.</font>
<br>
<font size=2>	arXiv:2205.01917, 2022.</font>
<a href='https://arxiv.org/abs/2205.01917'>[paper]</a> 
</p>

<p>
<font size=3><b>Prefix Conditioning Unifies Language and Label Supervision.</b></font>
<br>
<font size=2>Kuniaki Saito, Kihyuk Sohn, Xiang Zhang, Chun-Liang Li, Chen-Yu Lee, Kate Saenko, Tomas Pfister.</font>
<br>
<font size=2>arXiv:2206.01125, 2022.</font>
<a href='https://arxiv.org/abs/2206.01125'>[paper]</a> 
</p>

<p>
<font size=3><b>MaskCLIP: Masked Self-Distillation Advances Contrastive Language-Image Pretraining.</b></font>
<br>
<font size=2>Xiaoyi Dong, Yinglin Zheng, Jianmin Bao, Ting Zhang, Dongdong Chen, Hao Yang, Ming Zeng, Weiming Zhang, Lu Yuan, Dong Chen, Fang Wen, Nenghai Yu.</font>
<br>
<font size=2>arXiv:2208.12262, 2021</font>
<a href='hhttps://arxiv.org/abs/2208.12262'>[paper]</a>
</p>

<p>
<font size=3><b>[BASIC] Combined Scaling for Open-Vocabulary Image Classification.</b></font>
<br>
<font size=2>Hieu Pham, Zihang Dai, Golnaz Ghiasi, Kenji Kawaguchi, Hanxiao Liu, Adams Wei Yu, Jiahui Yu, Yi-Ting Chen, Minh-Thang Luong, Yonghui Wu, Mingxing Tan, Quoc V. Le.</font>
<br>
<font size=2>	arXiv:2111.10050, 2022.</font>
<a href='https://arxiv.org/abs/2111.10050'>[paper]</a> 
</p>

<p>
<font size=3><b>[LIMoE] Multimodal Contrastive Learning with LIMoE: the Language-Image Mixture of Experts.</b></font>
<br>
<font size=2>Basil Mustafa, Carlos Riquelme, Joan Puigcerver, Rodolphe Jenatton, Neil Houlsby.</font>
<br>
<font size=2>	arXiv:2206.02770, 2022.</font>
<a href='https://arxiv.org/abs/2206.02770'>[paper]</a> 
</p>



<p>
<font size=3><b>MURAL: Multimodal, Multitask Retrieval Across Languages.</b></font>
<br>
<font size=2>Aashi Jain, Mandy Guo, Krishna Srinivasan, Ting Chen, Sneha Kudugunta, Chao Jia, Yinfei Yang, Jason Baldridge.</font>
<br>
<font size=2>arXiv:2109.05125, 2022.</font>
<a href='https://arxiv.org/abs/2109.05125'>[paper]</a> 
</p>



<p>
<font size=3><b>PaLI: A Jointly-Scaled Multilingual Language-Image Model.</b></font>
<br>
<font size=2>Xi Chen, Xiao Wang, Soravit Changpinyo, AJ Piergiovanni, Piotr Padlewski, Daniel Salz, Sebastian Goodman, Adam Grycner, Basil Mustafa, Lucas Beyer, Alexander Kolesnikov, Joan Puigcerver, Nan Ding, Keran Rong, Hassan Akbari, Gaurav Mishra, Linting Xue, Ashish Thapliyal, James Bradbury, Weicheng Kuo, Mojtaba Seyedhosseini, Chao Jia, Burcu Karagol Ayan, Carlos Riquelme, Andreas Steiner, Anelia Angelova, Xiaohua Zhai, Neil Houlsby, Radu Soricut.</font>
<br>
<font size=2>	arXiv:2209.06794, 2022.</font>
<a href='https://arxiv.org/abs/2209.06794'>[paper]</a> 
</p>




## :orange_book: Object Detection in the Wild

<p>
<font size=3><b>Open-Vocabulary Object Detection Using Captions.</b></font>
<br>
<font size=2>Alireza Zareian, Kevin Dela Rosa, Derek Hao Hu, Shih-Fu Chang.</font>
<br>
<font size=2>CVPR 2021.</font>
<a href='https://arxiv.org/abs/2011.10678'>[paper]</a> 
</p>

<p>
<font size=3><b>MDETR: Modulated Detection for End-to-End Multi-Modal Understanding.</b></font>
<br>
<font size=2>Aishwarya Kamath, Mannat Singh, Yann LeCun, Gabriel Synnaeve, Ishan Misra, Nicolas Carion.</font>
<br>
<font size=2>ICCV 2021.</font>
<a href='https://arxiv.org/abs/2104.12763'>[paper]</a> <a href='https://github.com/ashkamath/mdetr'>[code]</a>    
</p>

<p>
<font size=3><b>[VILD] 
Open-vocabulary Object Detection via Vision and Language Knowledge Distillation.
</b></font>
<br>
<font size=2>Xiuye Gu, Tsung-Yi Lin, Weicheng Kuo, Yin Cui.</font>
<br>
<font size=2>ICLR 2022.</font>
<a href='https://arxiv.org/abs/2104.13921'>[paper]</a>
</p>


<p>
<font size=3><b>[GLIP] Grounded Language-Image Pre-training.</b></font>
<br>
<font size=2>Liunian Harold Li, Pengchuan Zhang, Haotian Zhang, Jianwei Yang, Chunyuan Li, Yiwu Zhong, Lijuan Wang, Lu Yuan, Lei Zhang, Jenq-Neng Hwang, Kai-Wei Chang, Jianfeng Gao</font>
<br>
<font size=2>CVPR 2022.</font>
<a href='https://arxiv.org/abs/2112.03857'>[paper]</a> <a href='https://github.com/microsoft/GLIP'>[code]</a>    
</p>

<p>
<font size=3><b>RegionCLIP: Region-based Language-Image Pretraining.</b></font>
<br>
<font size=2>Yiwu Zhong, Jianwei Yang, Pengchuan Zhang, Chunyuan Li, Noel Codella, Liunian Harold Li, Luowei Zhou, Xiyang Dai, Lu Yuan, Yin Li, Jianfeng Gao.</font>
<br>
<font size=2>CVPR 2022.</font>
<a href='https://arxiv.org/abs/2112.09106'>[paper]</a> <a href='https://github.com/microsoft/RegionCLIP'>[code]</a>    
</p>



<p>
<font size=3><b>[OV-DETR] Open-Vocabulary DETR with Conditional Matching Yuhang.</b></font>
<br>
<font size=2>Yuhang Zang, Wei Li, Kaiyang Zhou, Chen Huang, Chen Change Loy.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2203.11876'>[paper]</a> <a href='https://github.com/yuhangzang/ov-detr'>[code]</a>    
</p>



<p>
<font size=3><b>[OWL-ViT] Simple Open-Vocabulary Object Detection with Vision Transformers.</b></font>
<br>
<font size=2>Matthias Minderer, Alexey Gritsenko, Austin Stone, Maxim Neumann, Dirk Weissenborn, Alexey Dosovitskiy, Aravindh Mahendran, Anurag Arnab, Mostafa Dehghani, Zhuoran Shen, Xiao Wang, Xiaohua Zhai, Thomas Kipf, Neil Houlsby.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2205.06230'>[paper]</a>     
</p>


<p>
<font size=3><b>[Detic] Detecting Twenty-thousand Classes using Image-level Supervision.</b></font>
<br>
<font size=2>Xingyi Zhou, Rohit Girdhar, Armand Joulin, Philipp Krähenbühl, Ishan Misra.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2201.02605'>[paper]</a> <a href='https://github.com/facebookresearch/Detic/'>[code]</a>        
</p>


<p>
<font size=3><b>X-DETR: A Versatile Architecture for Instance-wise Vision-Language Tasks.</b></font>
<br>
<font size=2>Zhaowei Cai, Gukyeong Kwon, Avinash Ravichandran, Erhan Bas, Zhuowen Tu, Rahul Bhotika, Stefano Soatto.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2204.05626'>[paper]</a>     
</p>

<p>
<font size=3><b>FindIt: Generalized Localization with Natural Language Queries.</b></font>
<br>
<font size=2>Weicheng Kuo, Fred Bertsch, Wei Li, AJ Piergiovanni, Mohammad Saffar, Anelia Angelova.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2203.17273'>[paper]</a>     
</p>


<p>
<font size=3><b>Open Vocabulary Object Detection with Pseudo Bounding-Box Labels.</b></font>
<br>
<font size=2>Mingfei Gao, Chen Xing, Juan Carlos Niebles, Junnan Li, Ran Xu, Wenhao Liu, Caiming Xiong.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2111.09452'>[paper]</a> <a href='https://github.com/salesforce/PB-OVD'>[code]</a>    <a href='https://blog.salesforceairesearch.com/pb-ovd-open-vocabulary-object-detector/'>[blog]</a>        
</p>



<p>
<font size=3><b>PromptDet: Towards Open-vocabulary Detection using Uncurated Images.</b></font>
<br>
<font size=2>Chengjian Feng, Yujie Zhong, Zequn Jie, Xiangxiang Chu, Haibing Ren, Xiaolin Wei, Weidi Xie, Lin Ma.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2203.16513'>[paper]</a> <a href='https://fcjian.github.io/promptdet/'>[code]</a>        
</p>

<p>
<font size=3><b>Class-agnostic Object Detection with Multi-modal Transformer.</b></font>
<br>
<font size=2>Muhammad Maaz, Hanoona Rasheed, Salman Khan, Fahad Shahbaz Khan, Rao Muhammad Anwer and Ming-Hsuan Yang.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2111.11430'>[paper]</a> <a href='https://github.com/mmaaz60/mvits_for_class_agnostic_od'>[code]</a>    
</p>

<p>
<font size=3><b>[Object Centric OVD] -- Bridging the Gap between Object and Image-level Representations for Open-Vocabulary Detection.</b></font>
<br>
<font size=2>Hanoona Rasheed, Muhammad Maaz, Muhammad Uzair Khattak, Salman Khan, Fahad Shahbaz Khan.</font>
<br>
<font size=2>NeurIPS 2022</font>
<a href='https://arxiv.org/abs/2207.03482'>[paper]</a> <a href='https://github.com/hanoonaR/object-centric-ovd'>[code]</a>    
</p>

<p>
<font size=3><b>[GLIPv2] Unifying Localization and Vision-Language Understanding.</b></font>
<br>
<font size=2>Haotian Zhang, Pengchuan Zhang, Xiaowei Hu, Yen-Chun Chen, Liunian Harold Li, Xiyang Dai, Lijuan Wang, Lu Yuan, Jenq-Neng Hwang, Jianfeng Gao.</font>
<br>
<font size=2>NeurIPS 2022</font>
<a href='https://arxiv.org/abs/2206.05836'>[paper]</a> <a href='https://github.com/microsoft/GLIP'>[code]</a>    
</p>

<p>
<font size=3><b>[FIBER] Coarse-to-Fine Vision-Language Pre-training with Fusion in the Backbone.</b></font>
<br>
<font size=2>Zi-Yi Dou, Aishwarya Kamath, Zhe Gan, Pengchuan Zhang, Jianfeng Wang, Linjie Li, Zicheng Liu, Ce Liu, Yann LeCun, Nanyun Peng, Jianfeng Gao, Lijuan Wang.</font>
<br>
<font size=2>NeurIPS 2022</font>
<a href='https://arxiv.org/abs/2206.07643'>[paper]</a> <a href='https://github.com/microsoft/FIBER'>[code]</a>    
</p>

<p>
<font size=3><b>[DetCLIP] Dictionary-Enriched Visual-Concept Paralleled Pre-training for Open-world Detection.</b></font>
<br>
<font size=2> Lewei Yao, Jianhua Han, Youpeng Wen, Xiaodan Liang, Dan Xu, Wei zhang, Zhenguo Li, Chunjing Xu, Hang Xu.</font>
<br>
<font size=2>NeurIPS 2022</font>
<a href='https://arxiv.org/abs/2209.09407v1'>[paper]</a>  
</p>

<p>
<font size=3><b>OmDet: Language-Aware Object Detection with Large-scale Vision-Language Multi-dataset Pre-training.</b></font>
<br>
<font size=2>Tiancheng Zhao, Peng Liu, Xiaopeng Lu, Kyusong Lee</font>
<br>
<font size=2>arxiv:2209.0594</font>
<a href='https://arxiv.org/abs/2209.05946'>[paper]</a> 
</p>


## :orange_book: Segmentation in the Wild


<p>
<font size=3><b>PhraseCut: Language-based Image Segmentation in the Wild
</b></font>
<br>
<font size=2>Chenyun Wu, Zhe Lin, Scott Cohen, Trung Bui, Subhransu Maji.</font>
<br>
<font size=2>CVPR 2022.</font>
<a href='https://arxiv.org/abs/2008.01187'>[paper]</a>  <a href='https://people.cs.umass.edu/~chenyun/publication/phrasecut/'>[project]</a>     
</p>


<p>
<font size=3><b>GroupViT: Semantic Segmentation Emerges from Text Supervision
</b></font>
<br>
<font size=2>Jiarui Xu, Shalini De Mello, Sifei Liu, Wonmin Byeon, Thomas Breuel, Jan Kautz, Xiaolong Wang.</font>
<br>
<font size=2>CVPR 2022.</font>
<a href='https://arxiv.org/abs/2202.11094'>[paper]</a>  <a href='https://github.com/NVlabs/GroupViT/'>[code]</a>   <a href='https://jerryxu.net/GroupViT/'>[project]</a>     
</p>

<p>
<font size=3><b>[CLIPSeg] 
Image Segmentation Using Text and Image Prompts.
</b></font>
<br>
<font size=2>Timo Lüddecke, Alexander S. Ecker.</font>
<br>
<font size=2>CVPR 2022.</font>
<a href='https://arxiv.org/abs/2112.10003'>[paper]</a>  <a href='https://github.com/timojl/clipseg'>[code]</a>    
</p>


<p>
<font size=3><b>DenseCLIP: Language-Guided Dense Prediction with Context-Aware Prompting.</b></font>
<br>
<font size=2>Yongming Rao*, Wenliang Zhao*, Guangyi Chen, Yansong Tang, Zheng Zhu, Guan Huang, Jie Zhou, Jiwen Lu.</font>
<br>
<font size=2>CVPR, 2022</font>
<a href='https://arxiv.org/abs/2112.01518'>[paper]</a>  <a href='https://github.com/raoyongming/DenseCLIP'>[code]</a>    
</p>

<p>
<font size=3><b>[OpenSeg] 
Scaling Open-Vocabulary Image Segmentation with Image-Level Labels.
</b></font>
<br>
<font size=2>Golnaz Ghiasi, Xiuye Gu, Yin Cui, Tsung-Yi Lin.</font>
<br>
<font size=2>ECCV 2022.</font>
<a href='https://arxiv.org/abs/2112.12143'>[paper]</a>
</p>


<p>
<font size=3><b>A Simple Baseline for Zero-shot Semantic Segmentation with Pre-trained Vision-language Model.</b></font>
<br>
<font size=2>Mengde Xu, Zheng Zhang, Fangyun Wei, Yutong Lin, Yue Cao, Han Hu, Xiang Bai.</font>
<br>
<font size=2>arXiv:2112.14757, 2021</font>
<a href='https://arxiv.org/abs/2112.14757'>[paper]</a>
</p>

<p>
<font size=3><b>[MaskCLIP] Extract Free Dense Labels from CLIP.</b></font>
<br>
<font size=2>Chong Zhou, Chen Change Loy, Bo Dai.</font>
<br>
<font size=2>ECCV 2022</font>
<a href='https://arxiv.org/abs/2112.01071'>[paper]</a> <a href='https://github.com/chongzhou96/MaskCLIP'>[code]</a>    
</p>


<p>
<font size=3><b>Open-Vocabulary Panoptic Segmentation with MaskCLIP.</b></font>
<br>
<font size=2>Zheng Ding, Jieke Wang, Zhuowen Tu.</font>
<br>
<font size=2>arXiv:2208.08984, 2022</font>
<a href='https://arxiv.org/abs/2208.08984'>[paper]</a>
</p>






## :orange_book: Video Classification in the Wild

<p>
<font size=3><b>Expanding Language-Image Pretrained Models for General Video Recognition.</b></font>
<br>
<font size=2>Bolin Ni, Houwen Peng, Minghao Chen, Songyang Zhang, Gaofeng Meng, Jianlong Fu, Shiming Xiang, Haibin Ling.</font>
<br>
<font size=2>ECCV 2022</font>
<a href='https://arxiv.org/abs/2208.02816'>[paper]</a> <a href='https://github.com/microsoft/VideoX'>[code]</a>    
</p>

<p>
<font size=3><b>Multimodal Open-Vocabulary Video Classification via Pre-Trained Vision and Language Models.</b></font>
<br>
<font size=2>Rui Qian, Yeqing Li, Zheng Xu, Ming-Hsuan Yang, Serge Belongie, Yin Cui.</font>
<br>
<font size=2>	arXiv:2207.07646</font>
<a href='https://arxiv.org/abs/2207.07646v1'>[paper]</a>
</p>


## :orange_book: Other Visual Recognition in the Wild

<p>
<font size=3><b>RLIP: Relational Language-Image Pre-training for Human-Object Interaction Detection.</b></font>
<br>
<font size=2>Hangjie Yuan, Jianwen Jiang, Samuel Albanie, Tao Feng, Ziyuan Huang, Dong Ni, Mingqian Tang.</font>
<br>
<font size=2>NeurIPS 2022</font>
<a href='https://arxiv.org/abs/2209.01814'>[paper]</a> <a href='https://github.com/JacobYuan7/RLIP'>[code]</a>    
</p>

# :snowflake: Papers on Efficient Model Adaptation

## :blue_book: Parameter-Efficient Methods

# :beers: Acknowledgements

We thank all the authors above for their great works! Related Reading List 

- [[Awesome Detection Transformer]](https://github.com/IDEACVR/awesome-detection-transformer) 
