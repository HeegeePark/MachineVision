# LBP 패턴
```
import numpy as np

def solution(img):
    '''
    3×3 이미지를 입력 받아 LBP 패턴을 생성한 후 
    10진수 값으로 반환해주는 함수 작성
    
    <조건 1>
    패턴 생성 순서 = [4 3 2
                      5 - 1
                      6 7 8]    
                      
        - *조교님 정답 유출 가능한 패턴 생성 순서로 연산하였습니다.
            
            패턴 생성 순서 = [5 6 7
                              4 - 8
                              3 2 1]    
    
    2^7   2^6   2^5   2^4   2^3   2^2   2^1   2^0
     8     7     6     5     4     3     2     1
     
     
    <조건 2>
    if neighbor_pixel > center:
        1
    else:
        0
    '''   
    lbp = 0
    img = np.ndarray.flatten(img)   # 1차원 직선 배열로 변경
    
    # 이미지 사이즈 및 센터위치 구하기
    img_size = len(img)
    center = int(img_size/2)
    
    # LBP 패턴 생성
    rule = [8,7,6,3,0,1,2,5]  # 패턴 생성 순서
    lbp_array = np.zeros((img_size - 1), dtype=int)
            
    for i in range(len(lbp_array)) :
        if img[rule[i]] > img[center]:
            lbp_array[i] = 1
    
    # 십진수 변환
    where_1=np.where(lbp_array == 1)
    for i in range(len(where_1[0])) :
        lbp += 2**(len(lbp_array) - where_1[0][i] - 1)        
    
    print(lbp)
```
