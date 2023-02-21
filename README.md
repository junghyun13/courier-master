# courier-master
# python
첫째 줄에는 레일의 개수 N, 택배 q박스의 무게 M, 일의 시행 횟수 K가 주어진다. 그 다음 줄에는 Ni개의 택배 레일의 전용 무게가 주어진다. 레일 순서대로 택배를 담되, 박스무게를 초과하지 않은 만큼 담아서 이동하게 되면 1번 일한 것으로 쳐준다.  총 K번 일을 하는데 최소한의 무게로 일을 할 수 있게를 도와주는 프로그램을 작성해보자!


import sys
from itertools import permutations
n,m,k=map(int,sys.stdin.readline().split())
q=list(map(int,sys.stdin.readline().split()))
rail=list(permutations(q,n)) #q에서 n개의 순열을 리스트에 넣는다
def solution(rail):
  i=0
  check=0
  for j in range(k):
    box=0
    while True:
      box+=rail[i]
      i=(i+1)%n #i가 마지막 rail값이 되면 처음으로 
      if box+rail[i]>m:
        break
    check+=box
  return check
answer=[]
for t in rail:
  answer.append(solution(t))
print(min(answer))
