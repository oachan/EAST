# CXXFLAGS = -I include  -std=c++11 -O3 $(shell python3.6-config --cflags)
CXXFLAGS = -I include  -std=c++11 -O3 -I/home/458928/anaconda3/envs/OCR_tensorflow/include/python3.6m -I/home/458928/anaconda3/envs/OCR_tensorflow/include/python3.6m  -Wno-unused-result -Wsign-compare -march=nocona -mtune=haswell -ftree-vectorize -fPIC -fstack-protector-strong -O3 -ffunction-sections -pipe -isystem /home/458928/anaconda3/envs/OCR_tensorflow/include -fdebug-prefix-map=/tmp/build/80754af9/python_1588903631989/work=/usr/local/src/conda/python-3.6.10 -fdebug-prefix-map=/home/458928/anaconda3/envs/OCR_tensorflow=/usr/local/src/conda-prefix -fuse-linker-plugin -ffat-lto-objects -flto-partition=none -flto -DNDEBUG -fwrapv -O3 -Wall
LDFLAGS = $(shell python3.6-config --ldflags)

DEPS = lanms.h $(shell find include -xtype f)
CXX_SOURCES = adaptor.cpp include/clipper/clipper.cpp

LIB_SO = adaptor.so

$(LIB_SO): $(CXX_SOURCES) $(DEPS)
	$(CXX) -o $@ $(CXXFLAGS) $(LDFLAGS) $(CXX_SOURCES) --shared -fPIC

clean:
	rm -rf $(LIB_SO)
