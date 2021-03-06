# Solutions ch. 10 - Artificial neural networks {#solutions-ann}

Solutions to exercises of chapter \@ref(ann).

## Exercise 1


```r
library("neuralnet")
 
#To create a neural network to perform square root

#Generate 50 random numbers uniformly distributed between 0 and 100
#And store them as a dataframe
traininginput <-  as.data.frame(runif(50, min=0, max=100))
trainingoutput <- sqrt(traininginput)
 
#Column bind the data into one variable
trainingdata <- cbind(traininginput,trainingoutput)
colnames(trainingdata) <- c("Input","Output")
 
#Train the neural network
#Will have 10 hidden layers
#Threshold is a numeric value specifying the threshold for the partial
#derivatives of the error function as stopping criteria.
net.sqrt <- neuralnet(Output~Input,trainingdata, hidden=10, threshold=0.01)
print(net.sqrt)
```

```
## $call
## neuralnet(formula = Output ~ Input, data = trainingdata, hidden = 10, 
##     threshold = 0.01)
## 
## $response
##      Output
## 1  7.999302
## 2  7.679743
## 3  5.712257
## 4  8.450774
## 5  2.704332
## 6  7.469555
## 7  9.382828
## 8  4.640093
## 9  6.514652
## 10 4.756397
## 11 5.387100
## 12 7.773787
## 13 4.007812
## 14 5.616837
## 15 7.431411
## 16 5.102096
## 17 9.942605
## 18 8.135916
## 19 1.615092
## 20 7.752434
## 21 8.463426
## 22 5.457865
## 23 5.027473
## 24 9.574040
## 25 4.703425
## 26 9.330075
## 27 4.111931
## 28 9.397304
## 29 6.278908
## 30 2.992013
## 31 4.155768
## 32 1.039876
## 33 9.962122
## 34 1.091506
## 35 7.157701
## 36 6.349765
## 37 9.028152
## 38 9.695076
## 39 9.413394
## 40 3.302956
## 41 9.172890
## 42 6.557068
## 43 3.183634
## 44 6.250623
## 45 9.740172
## 46 4.743667
## 47 6.008217
## 48 6.674838
## 49 7.617343
## 50 9.571043
## 
## $covariate
##                
##  [1,] 63.988838
##  [2,] 58.978448
##  [3,] 32.629886
##  [4,] 71.415581
##  [5,]  7.313410
##  [6,] 55.794259
##  [7,] 88.037453
##  [8,] 21.530465
##  [9,] 42.440693
## [10,] 22.623308
## [11,] 29.020847
## [12,] 60.431758
## [13,] 16.062554
## [14,] 31.548857
## [15,] 55.225866
## [16,] 26.031386
## [17,] 98.855394
## [18,] 66.193129
## [19,]  2.608523
## [20,] 60.100227
## [21,] 71.629574
## [22,] 29.788293
## [23,] 25.275488
## [24,] 91.662240
## [25,] 22.122205
## [26,] 87.050299
## [27,] 16.907973
## [28,] 88.309323
## [29,] 39.424681
## [30,]  8.952143
## [31,] 17.270406
## [32,]  1.081342
## [33,] 99.243870
## [34,]  1.191386
## [35,] 51.232684
## [36,] 40.319516
## [37,] 81.507535
## [38,] 93.994495
## [39,] 88.611982
## [40,] 10.909516
## [41,] 84.141912
## [42,] 42.995138
## [43,] 10.135522
## [44,] 39.070291
## [45,] 94.870954
## [46,] 22.502376
## [47,] 36.098670
## [48,] 44.553463
## [49,] 58.023917
## [50,] 91.604870
## 
## $model.list
## $model.list$response
## [1] "Output"
## 
## $model.list$variables
## [1] "Input"
## 
## 
## $err.fct
## function (x, y) 
## {
##     1/2 * (y - x)^2
## }
## <bytecode: 0x558e4ff511b8>
## <environment: 0x558e4ff53928>
## attr(,"type")
## [1] "sse"
## 
## $act.fct
## function (x) 
## {
##     1/(1 + exp(-x))
## }
## <bytecode: 0x558e4ff4c888>
## <environment: 0x558e4ff4fd88>
## attr(,"type")
## [1] "logistic"
## 
## $linear.output
## [1] TRUE
## 
## $data
##        Input   Output
## 1  63.988838 7.999302
## 2  58.978448 7.679743
## 3  32.629886 5.712257
## 4  71.415581 8.450774
## 5   7.313410 2.704332
## 6  55.794259 7.469555
## 7  88.037453 9.382828
## 8  21.530465 4.640093
## 9  42.440693 6.514652
## 10 22.623308 4.756397
## 11 29.020847 5.387100
## 12 60.431758 7.773787
## 13 16.062554 4.007812
## 14 31.548857 5.616837
## 15 55.225866 7.431411
## 16 26.031386 5.102096
## 17 98.855394 9.942605
## 18 66.193129 8.135916
## 19  2.608523 1.615092
## 20 60.100227 7.752434
## 21 71.629574 8.463426
## 22 29.788293 5.457865
## 23 25.275488 5.027473
## 24 91.662240 9.574040
## 25 22.122205 4.703425
## 26 87.050299 9.330075
## 27 16.907973 4.111931
## 28 88.309323 9.397304
## 29 39.424681 6.278908
## 30  8.952143 2.992013
## 31 17.270406 4.155768
## 32  1.081342 1.039876
## 33 99.243870 9.962122
## 34  1.191386 1.091506
## 35 51.232684 7.157701
## 36 40.319516 6.349765
## 37 81.507535 9.028152
## 38 93.994495 9.695076
## 39 88.611982 9.413394
## 40 10.909516 3.302956
## 41 84.141912 9.172890
## 42 42.995138 6.557068
## 43 10.135522 3.183634
## 44 39.070291 6.250623
## 45 94.870954 9.740172
## 46 22.502376 4.743667
## 47 36.098670 6.008217
## 48 44.553463 6.674838
## 49 58.023917 7.617343
## 50 91.604870 9.571043
## 
## $exclude
## NULL
## 
## $net.result
## $net.result[[1]]
##           [,1]
##  [1,] 7.995789
##  [2,] 7.674736
##  [3,] 5.717007
##  [4,] 8.451986
##  [5,] 2.696557
##  [6,] 7.464572
##  [7,] 9.389452
##  [8,] 4.636127
##  [9,] 6.516467
## [10,] 4.753220
## [11,] 5.389975
## [12,] 7.769028
## [13,] 4.005833
## [14,] 5.621219
## [15,] 7.426514
## [16,] 5.102246
## [17,] 9.929306
## [18,] 8.133570
## [19,] 1.613746
## [20,] 7.747604
## [21,] 8.464797
## [22,] 5.461289
## [23,] 5.026849
## [24,] 9.577121
## [25,] 4.699857
## [26,] 9.337225
## [27,] 4.108820
## [28,] 9.403753
## [29,] 6.282515
## [30,] 2.994833
## [31,] 4.152269
## [32,] 1.042267
## [33,] 9.947520
## [34,] 1.090505
## [35,] 7.154074
## [36,] 6.352889
## [37,] 9.035538
## [38,] 9.694342
## [39,] 9.419631
## [40,] 3.309331
## [41,] 9.180678
## [42,] 6.558515
## [43,] 3.189577
## [44,] 6.254407
## [45,] 9.737655
## [46,] 4.740392
## [47,] 6.013047
## [48,] 6.675228
## [49,] 7.612261
## [50,] 9.574202
## 
## 
## $weights
## $weights[[1]]
## $weights[[1]][[1]]
##          [,1]        [,2]         [,3]        [,4]        [,5]       [,6]
## [1,] 17.45756 -0.03480288 -0.004262535 -0.61566375 -1.18516184  0.3813828
## [2,] 17.90798 -0.04717407  0.078630008  0.08937024  0.03177438 -0.3019641
##            [,7]      [,8]        [,9]      [,10]
## [1,] -2.7477476 -14.70377  0.85875024 -0.5474320
## [2,]  0.0316136  10.96269 -0.03551829  0.0432925
## 
## $weights[[1]][[2]]
##             [,1]
##  [1,]  1.7874065
##  [2,] -0.4323430
##  [3,] -1.6307006
##  [4,]  0.8227102
##  [5,]  1.9256264
##  [6,]  2.2012290
##  [7,] -1.9312278
##  [8,]  4.5230676
##  [9,]  0.1780150
## [10,] -1.3651657
## [11,]  1.1688972
## 
## 
## 
## $generalized.weights
## $generalized.weights[[1]]
##                [,1]
##  [1,] -0.0011257778
##  [2,] -0.0012732022
##  [3,] -0.0032555481
##  [4,] -0.0009511381
##  [5,] -0.0423228908
##  [6,] -0.0013844653
##  [7,] -0.0006686095
##  [8,] -0.0064281615
##  [9,] -0.0021167831
## [10,] -0.0059387733
## [11,] -0.0039548171
## [12,] -0.0012273349
## [13,] -0.0102350120
## [14,] -0.0034429361
## [15,] -0.0014060913
## [16,] -0.0047305801
## [17,] -0.0005300659
## [18,] -0.0010693187
## [19,] -0.2634314103
## [20,] -0.0012375542
## [21,] -0.0009466931
## [22,] -0.0037873662
## [23,] -0.0049639263
## [24,] -0.0006192004
## [25,] -0.0061557610
## [26,] -0.0006826564
## [27,] -0.0094291346
## [28,] -0.0006647871
## [29,] -0.0023840619
## [30,] -0.0286649468
## [31,] -0.0091164111
## [32,] -8.2966308600
## [33,] -0.0005255566
## [34,] -5.3683211584
## [35,] -0.0015763735
## [36,] -0.0022988521
## [37,] -0.0007669083
## [38,] -0.0005890764
## [39,] -0.0006605549
## [40,] -0.0197956501
## [41,] -0.0007256621
## [42,] -0.0020733334
## [43,] -0.0226714180
## [44,] -0.0024193360
## [45,] -0.0005780701
## [46,] -0.0059900489
## [47,] -0.0027541573
## [48,] -0.0019593005
## [49,] -0.0013049129
## [50,] -0.0006199572
## 
## 
## $startweights
## $startweights[[1]]
## $startweights[[1]][[1]]
##             [,1]       [,2]      [,3]      [,4]       [,5]       [,6]
## [1,] -0.08895678 -0.6657007 0.7027419 0.6895249 0.06907491 -0.7379227
## [2,]  0.92457554 -0.3754092 0.1740861 1.5494126 1.19983016 -1.6065634
##            [,7]         [,8]        [,9]       [,10]
## [1,] -0.8710877 -0.008041893 -0.04088576 -0.56192741
## [2,]  1.4674249  0.761402442 -0.92774640  0.08642731
## 
## $startweights[[1]][[2]]
##              [,1]
##  [1,]  0.98337360
##  [2,] -1.23637593
##  [3,] -0.70225856
##  [4,] -0.15369182
##  [5,]  1.12175441
##  [6,]  0.24476055
##  [7,] -0.16931536
##  [8,]  1.41997294
##  [9,] -0.77967743
## [10,] -0.16934653
## [11,]  0.02352787
## 
## 
## 
## $result.matrix
##                                 [,1]
## error                   6.216324e-04
## reached.threshold       9.184971e-03
## steps                   2.997000e+03
## Intercept.to.1layhid1   1.745756e+01
## Input.to.1layhid1       1.790798e+01
## Intercept.to.1layhid2  -3.480288e-02
## Input.to.1layhid2      -4.717407e-02
## Intercept.to.1layhid3  -4.262535e-03
## Input.to.1layhid3       7.863001e-02
## Intercept.to.1layhid4  -6.156638e-01
## Input.to.1layhid4       8.937024e-02
## Intercept.to.1layhid5  -1.185162e+00
## Input.to.1layhid5       3.177438e-02
## Intercept.to.1layhid6   3.813828e-01
## Input.to.1layhid6      -3.019641e-01
## Intercept.to.1layhid7  -2.747748e+00
## Input.to.1layhid7       3.161360e-02
## Intercept.to.1layhid8  -1.470377e+01
## Input.to.1layhid8       1.096269e+01
## Intercept.to.1layhid9   8.587502e-01
## Input.to.1layhid9      -3.551829e-02
## Intercept.to.1layhid10 -5.474320e-01
## Input.to.1layhid10      4.329250e-02
## Intercept.to.Output     1.787406e+00
## 1layhid1.to.Output     -4.323430e-01
## 1layhid2.to.Output     -1.630701e+00
## 1layhid3.to.Output      8.227102e-01
## 1layhid4.to.Output      1.925626e+00
## 1layhid5.to.Output      2.201229e+00
## 1layhid6.to.Output     -1.931228e+00
## 1layhid7.to.Output      4.523068e+00
## 1layhid8.to.Output      1.780150e-01
## 1layhid9.to.Output     -1.365166e+00
## 1layhid10.to.Output     1.168897e+00
## 
## attr(,"class")
## [1] "nn"
```

```r
#Plot the neural network
plot(net.sqrt)
 
#Test the neural network on some training data
testdata <- as.data.frame((1:10)^2) #Generate some squared numbers
net.results <- compute(net.sqrt, testdata) #Run them through the neural network
 
#See what properties net.sqrt has
ls(net.results)
```

```
## [1] "net.result" "neurons"
```

```r
#see the results
print(net.results$net.result)
```

```
##           [,1]
##  [1,] 1.015143
##  [2,] 1.967392
##  [3,] 3.003014
##  [4,] 3.998117
##  [5,] 4.999093
##  [6,] 6.004849
##  [7,] 6.997524
##  [8,] 7.996492
##  [9,] 9.007221
## [10,] 9.982728
```

```r
#Display a better version of the results
cleanoutput <- cbind(testdata,sqrt(testdata),
                         as.data.frame(net.results$net.result))
colnames(cleanoutput) <- c("Input","Expected Output","Neural Net Output")
print(cleanoutput)
```

```
##    Input Expected Output Neural Net Output
## 1      1               1          1.015143
## 2      4               2          1.967392
## 3      9               3          3.003014
## 4     16               4          3.998117
## 5     25               5          4.999093
## 6     36               6          6.004849
## 7     49               7          6.997524
## 8     64               8          7.996492
## 9     81               9          9.007221
## 10   100              10          9.982728
```

*Acknowledgement: this example excercise was from* http://gekkoquant.com/2012/05/26/neural-networks-with-r-simple-example/ 

