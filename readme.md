# EAST: An Efficient and Accurate Scene Text Detector
個人使用的修改版本.

## 修改項目

### eval.py
1. test_data_path (line 11): 改成測試圖片的資料夾位置
2. output_dir (line 14): 改成輸出預測結果的位置
3. exts list (line 28): 若有特殊檔案格式照片, 可將其副檔名新增至此list內部
4. 將 `'{}.txt'.format(os.path.basename(im_fn).split('.')[0]))` 改成 `'box/{}.csv'.format(os.path.basename(im_fn)[:-4]))` (line 178):
  因為split會使得特定圖片檔名處理產生問題
5. ` f.write('{},{},{},{},{},{},{},{},transcript\r\n'.format(` (line 187): 額外輸出dummy label
6. 將 `img_path = os.path.join(FLAGS.output_dir, os.path.basename(im_fn))` 改成 `img_path = os.path.join(FLAGS.output_dir + '/img/', os.path.basename(im_fn))`: 輸出到img資料夾

### icdar.py
1. training_data_path (line 17): 改成訓練集資料夾位置
2. max_image_large_side (line 19): 在這份code中沒有使用到此參數
3. min_text_size (line 24~27): 改變這個參數可以抓取到比較小的文字特徵
4. 將 `txt_fn = im_fn.replace(os.path.basename(im_fn).split('.')[1], 'txt')` 改成 `txt_fn = im_fn[:-4] + '.csv'`
5. load_annotation 拼音校正 (原本為 load_annotaion)

### lanms/Makefile
將 `python3-config --cflags` 在terminal上面的結果貼到 `CXXFLAGS = -I include  -std=c++11 -O3 ......` 後面 (line 2)

### multigpu_train.py
1. restore (line 14): 要設為True, 才不會把原本的checkpoint給洗掉
2. `avg_time_per_step = (time.time() - start)/104` 改成 `avg_time_per_step = (time.time() - start)/10`: 純粹打錯typo
