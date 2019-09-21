# percentile stretching 함수 작성하기
```
def percentile_stretching(img, p_low, p_high):
     
	# Percentile Stretching 수행하기
    p_low = np.percentile(img, p_low)
    p_high = np.percentile(img, p_high)
    
    img_ptile = (img - p_low)/(p_high - p_low) * 255.0
    
    # 클리핑 처리
    img_ptile[img_ptile < 0] = 0
    img_ptile[img_ptile > 255.0] = 255.0
    
    # uint8 형변환
    img_ptile = img_ptile.astype(np.uint8)

    return img_ptile
```