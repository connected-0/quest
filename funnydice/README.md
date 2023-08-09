# AIFFEL Socar Campus Code Peer Review Templete

코더 : 이은영   

리뷰어 : 채화정

## PRT(PeerReviewTemplate)

각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- **[O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?**

> 정상적으로 작동합니다.
> 
- **[O] 주석을 보고 작성자의 코드가 이해되었나요?**

> 각 메서드마다의 역할에 대해 잘 적어주셨습니다.
> 
- **[X] 코드가 에러를 유발할 가능성이 없나요?**

> 입력받은 n값이 자연수가 아닐 때 에러가 발생할 수 있습니다.
> 
- **[O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?**

> 네. 주석을 통해서 이해한 내용을 확인할 수 있었습니다. 다만 더 효율적인 코드를 작성할 수 있었을 것이라는 아쉬움은 남습니다.
> 
- **[X] 코드가 간결한가요?**

> main() 함수가 작동할 때 setval()의 역할이 없기 때문에 해당 부분을 삭제해도 무방할 것 같습니다.
```
# Funnydice class 발췌
def setval(self, val):
    if val <= self.n:
        self.val=val
    else:  #예외처리
        msg = "주사위에 없는 숫자입니다. 주사위는 1 ~ {0}까지 있습니다.".format(self.n)
        raise ValueError(msg)

# main() 함수
def main():
    n = get_inputs()
    mydice = FunnyDice(n)
    mydice.throw()
    print(f"행운의 숫자는? {mydice.getval()}")

```
> 또한 굳이 index를 생성하지 않아도 랜덤값을 추출할 수 있어 해당 부분이 보완되면 좋을 것 같습니다.
> 

## 참고 링크 및 코드 개선

```
from random import randrange


class FunnyDice:
    def __init__(self, n=6):
        self.n = int(n)
        self.val = randrange(1, self.n+1)
        #생성자에 주사위 면 수만큼 리스트가 생성되고 랜덤함수로 인덱스를받아 val을 산출한다
        
    def throw(self): 
        self.val = randrange(1, self.n+1)
        return self.val
        #주사위를 던지면 랜덤으로 val이 생성된다

def get_inputs():
    n=int(input("주사위 면의 개수를 입력하세요 : "))
    if n <= 0:
        print('자연수를 입력하세요.\n오류가 발생하여, 기본값으로 자동실행 됩니다.')
        n = 6
    return n
    #사용자가 주사위 면의 개수를 입력할 수 있다

def main():
    n = get_inputs()
    mydice = FunnyDice(n)
    print(f"행운의 숫자는? {mydice.throw()}")
    #사용자에게 입력값을 받고 행운의 숫자를 출력한다

if __name__ == '__main__':
    main()
```

- - - -
**회고**   
은영님의 코드의 리뷰를 작성하며, 제 코드에서도 똑같이 발생할 수 있는 오류가 있다는 것을 도중에 깨달았습니다. 또한 코더의 의도를 파악하고자 노력하며 개선사항을 적으려고 하니, 보다 다양한 관점에서 시도를 해 볼 수 있었습니다. 제 리뷰가 은영님에게 100% 도움이 되지 않을 순 있지만, 리뷰를 작성하는 과정이 제게도 큰 공부가 된 것 같습니다~! 아직 코드가 길지 않고, 코더마다의 스타일에 큰 차이가 없어 코멘트가 짧지만 이후에는 더 다양한 관점에서 여러가지 피드백을 나눌 수 있을 것 같아 기대됩니다.   
   
   
2023/8/9 written by [채화정](https://github.com/HwajeongChae)