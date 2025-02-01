def ThreeSum(N,A):
  dic=set()
  for i in range(N):
    for j in range(i+1,N):
      for k in range(j+1,N):
        if A[i]+A[j]+A[k]==0:
          triplet=tuple(sorted([A[i],A[j],A[k]]))
          if triplet not in dic:
            dic.add(triplet)
  for ele in dic:
    print(*ele)
T=int(input())
for _ in range(T):
  N=int(input())
  A=list(map(int,input().split()))
  ThreeSum(N,A)