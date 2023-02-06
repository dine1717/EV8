## Assignment 6 - Advanced Concepts


Code Block :
  
  class CifarNet10(nn.Module):
  
      def __init__(self):
      
        super(CifarNet10, self).__init__()
        
        self.convblock1a = nn.Sequential(
            nn.Conv2d(in_channels = 3,out_channels = 16, dilation  = 1,padding = 1, kernel_size= (3,3)),                     # in 32, out 32, RF 3
            nn.ReLU(),
            nn.BatchNorm2d(16)
        )
        self.convblock1b = nn.Sequential(
            nn.Conv2d(in_channels = 16,out_channels = 16, dilation  = 1,padding = 1, kernel_size= (3,3)),                     # in 32, out 32, RF 3
            nn.ReLU(),
            nn.BatchNorm2d(16)
        )

        # Using stride 2 without dilation instead of maxpooling
        self.convpool1 = nn.Sequential(
            nn.Conv2d(in_channels = 16,out_channels = 16, dilation  = 1,padding = 1,kernel_size= (3,3),stride = 2), # in 32, out 16, RF ?
            nn.Conv2d(in_channels = 16,out_channels = 16, dilation  = 1,padding = 0,kernel_size= (1,1),stride = 1)   # to check if this can compensate for the mx pooling feature loss       
        )

        self.convblock2a = nn.Sequential(
            # nn.Conv2d(in_channels = 16,out_channels = 32, dilation  = 1,padding = 1,kernel_size= (3,3)),                    # in 16, out 16, RF ?
            nn.Conv2d(in_channels = 16,out_channels = 16,groups = 16, dilation  = 1,padding = 1,kernel_size= (3,3)),
            nn.Conv2d(in_channels = 16,out_channels = 32, dilation = 1,padding = 0,kernel_size= (1,1)), # 8, 8, 3  
            nn.ReLU(),
            nn.BatchNorm2d(32)
        ) # will the learning will be better in depth wise or in normal 3x3 convolutions?

        self.convblock2b = nn.Sequential(
            nn.Conv2d(in_channels = 32,out_channels = 32, dilation  = 1,padding = 1, kernel_size= (3,3)),                     # in 16, out 16, RF 3
            nn.ReLU(),
            nn.BatchNorm2d(32)
        )

        # Using stride 2 without dilation to simulate max pooling
        self.convpool2 = nn.Sequential(
            nn.Conv2d(in_channels = 32,out_channels = 32, dilation  = 1,padding = 1,kernel_size= (3,3),stride = 2),
            nn.Conv2d(in_channels = 32,out_channels = 32, dilation  = 1,padding = 0,kernel_size= (1,1),stride = 1)          # in 16, out 8, RF ?
        )


        self.convblock3a = nn.Sequential(
            # nn.Conv2d(in_channels = 32,out_channels = 64, dilation  = 1,padding = 1,kernel_size= (3,3)), 
            nn.Conv2d(in_channels = 32,out_channels = 32,groups = 32, dilation  = 1,padding = 1,kernel_size= (3,3)),        # in 8, out 8, RF ?
            nn.Conv2d(in_channels = 32,out_channels = 64, dilation = 1,padding = 0,kernel_size= (1,1)), # 8, 8, 3           # in 8, out 8, RF ?
            nn.ReLU(),
            nn.BatchNorm2d(64)
        )

        self.convblock3b = nn.Sequential(
            nn.Conv2d(in_channels = 64,out_channels = 64, dilation  = 2,padding = 2, kernel_size= (3,3)),                     # in 8, out 8, RF 3
            nn.ReLU(),
            nn.BatchNorm2d(64)
        )
        
        # using dilation to simulate maxpooling
        self.convpool3 = nn.Sequential(
            nn.Conv2d(in_channels = 64,out_channels = 64, dilation  = 1,padding = 1,kernel_size= (3,3),stride = 2),          # in 8, out 4, RF ?
            nn.Conv2d(in_channels = 64,out_channels = 64, dilation  = 1,padding = 0,kernel_size= (1,1),stride = 1)
        )


        self.convblock4a = nn.Sequential(
            # nn.Conv2d(in_channels = 128,out_channels = 128, dilation  = 1,padding = 1,kernel_size= (3,3)), 
            nn.Conv2d(in_channels = 64,out_channels = 64, groups = 64, dilation  = 1,padding = 1,kernel_size= (3,3)),    # in 4, out 4, RF ?
            nn.Conv2d(in_channels = 64,out_channels = 128, dilation  = 1,padding = 0,kernel_size= (1,1)),                  # in 4, out 4, RF ?
            nn.ReLU(),
            nn.BatchNorm2d(128)
        )

        self.convblock4b = nn.Sequential(
            # nn.Conv2d(in_channels = 128,out_channels = 128, dilation  = 1,padding = 1,kernel_size= (3,3)), 
            nn.Conv2d(in_channels = 128,out_channels = 128, groups = 128, dilation  = 1,padding = 1,kernel_size= (3,3)),    # in 4, out 4,, RF ?
            nn.Conv2d(in_channels = 128,out_channels = 256, dilation  = 1,padding = 0,kernel_size= (1,1)),                  # in 4, out 4, RF ?
            nn.ReLU(),
            nn.BatchNorm2d(256)
        )

        self.gap = nn.AvgPool2d(4)                                                                                          # in 3, out 1, RF ?
        self.convblockf = nn.Sequential(
            nn.Conv2d(in_channels=256, out_channels=10, kernel_size=(1, 1), padding=0, bias=False),
        ) 


    def forward(self, x):
        x = self.convblock1a(x)
        x = self.convblock1b(x)
        x = self.convpool1(x)
        x = self.convblock2a(x)
        x = self.convblock2b(x)
        x = self.convpool2(x)
        x = self.convblock3a(x)
        x1 = self.convblock3b(x)
        x = torch.add(x,x1)
        x = self.convpool3(x)
        x = self.convblock4a(x)
        x = self.convblock4b(x)
        x = self.gap(x)
        x = self.convblockf(x)
        x = x.view(-1, 10)
        return F.log_softmax(x, dim=-1)
       
       
  # Torch Summary:
  
  ![image](https://user-images.githubusercontent.com/73247157/217028937-42ab512b-9d60-4a6b-bae5-4b10d94c113f.png)


  # Albumentations
  
  ![image](https://user-images.githubusercontent.com/73247157/217029303-7f3d0b63-4923-4709-9430-0ff13fff4014.png)

  #  Epochs 

  ![image](https://user-images.githubusercontent.com/73247157/217029850-b787c048-83b9-4ea3-b363-270e76a0ceb8.png)

