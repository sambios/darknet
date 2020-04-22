cmake_minimum_required(VERSION 3.2)
project(darknet)

if (UNIX AND NOT APPLE)
set(CMAKE_C_FLAGS ${CMAKE_C_FLAGS} -Wall -Wno-unused-result -Wno-unknown-pragmas -Wfatal-errors -fPIC)
endif()

set(TOP ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${TOP}/include ${TOP}/src
        /usr/local/include)

set(CMAKE_C_FLAGS_DEBUG -o0)
set(CMAKE_C_FLAGS_RELEASE -ofast)

add_library(darknet_lib
        src/gemm.c
        src/utils.c
        src/cuda.c
        src/deconvolutional_layer.c
        src/convolutional_layer.c
        src/list.c
        src/image.c
        src/activations.c
        src/im2col.c
        src/col2im.c
        src/blas.c
        src/crop_layer.c
        src/dropout_layer.c
        src/maxpool_layer.c
        src/softmax_layer.c
        src/data.c
        src/matrix.c
        src/network.c
        src/connected_layer.c
        src/cost_layer.c
        src/parser.c
        src/option_list.c
        src/detection_layer.c
        src/route_layer.c
        src/upsample_layer.c
        src/box.c
        src/normalization_layer.c
        src/avgpool_layer.c
        src/layer.c
        src/local_layer.c
        src/shortcut_layer.c
        src/logistic_layer.c
        src/activation_layer.c
        src/rnn_layer.c
        src/gru_layer.c
        src/crnn_layer.c
        src/demo.c
        src/batchnorm_layer.c
        src/region_layer.c
        src/reorg_layer.c
        src/tree.c
        src/lstm_layer.c
        src/l2norm_layer.c
        src/yolo_layer.c
        src/iseg_layer.c
        src/image_opencv.cpp
        )

add_executable(darknet examples/art.c
        #examples/attention.c
        examples/captcha.c
        examples/cifar.c
        examples/classifier.c
        examples/coco.c
        examples/darknet.c
        examples/detector.c
        #examples/dice.c
        examples/go.c
        examples/instance-segmenter.c
        examples/lsd.c
        examples/nightmare.c
        examples/regressor.c
        examples/rnn.c
        #examples/rnn_vid.c
        examples/segmenter.c
        examples/super.c
        #examples/swag.c
        examples/tag.c
        #examples/voxel.c
        #examples/writing.c
        examples/yolo.c
        )

target_link_libraries(darknet darknet_lib)