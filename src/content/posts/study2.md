---
title: DFS와 BFS
published: 2024-07-01
tags: [Algorithm]
category: study
draft: false
---
# DFS(Depth-First Search) 깊이 우선 탐색
- 최대한 깊이 내려간 후 옆으로 이동한다.   
- 모든 노드를 방문한다.
- 너비 우선 탐색보다 좀 더 간단하다.
- 검색 속도는 너비 우선 탐색보다 느리다.
- 다음 줄로 넘어가기 전에 그 줄을 모두 탐색한다.   
스택, 재귀함수로 구현한다.

# BFS(Breadth-First Search) 너비 우선 탐색
- 루트노드(최상단 노드) 에서 가장 밀접한 노드 먼저 탐색한다.
- 두 노드 사이의 최단 경로를 찾고싶을 깨 사용한다.   
큐를 이용해 구현한다.

# 정리
모든 노드를 방문할 때는 BFS, DFS   
경로에 특징이 있으면 DFS   
최단거리는 BFS