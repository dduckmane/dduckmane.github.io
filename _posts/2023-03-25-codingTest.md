---
layout: single
title:  "[코딩테스트] 백준 14502번"
categories: CodingTest
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

- 그래프 탐색의 문제이다.
- 완전 탐색과 그래프 탐색을 같이 적용된 문제로 구현하기 까다로웠다.

```
// https://www.acmicpc.net/problem/14502
import java.io.*;
import java.util.StringTokenizer;

public class Main {
    static FastReader scan = new FastReader();
    static StringBuilder sb = new StringBuilder();


    static int N;
    static int M;
    static int[][] a;
    static int max = Integer.MIN_VALUE;
    static int[][] dir = new int[][]{% raw %}1, 0}, {-1, 0}, {0, 1}, {0,-1 {% endraw %};
    static boolean visited[][];
    static int block;

    static void input() {
        N = scan.nextInt();
        M = scan.nextInt();

        a = new int[N][M];
        visited = new boolean[N][M];

        for (int i = 0; i < N; i++) {
            for (int j = 0; j < M; j++) {
                a[i][j] = scan.nextInt();
                if (a[i][j] == 1) block ++;
            }
        }
    }
    static int sum_dfs = 0;
    static void dfs(int x, int y) {
        visited[x][y] = true;
        sum_dfs ++;

        for (int i = 0; i <4 ; i++) {
            int nx = x + dir[i][0];
            int ny = y + dir[i][1];

            if (nx < 0 || nx >=N || ny < 0 || ny >=M) continue;
            if (visited[nx][ny]) continue;

            if (a[nx][ny] == 0) {
                dfs(nx, ny);
            }
        }
    }
    static int sumFunc() {
        for (int i = 0; i <N; i++) {
            for (int j = 0; j < M; j++) {
                if (a[i][j] == 2) {
                    dfs(i, j);
                }
            }
        }

        return N*M - block - sum_dfs -3;
    }
    static void go(int x) {
        if (x == 3) {
            max = Math.max(sumFunc(), max);

            sum_dfs =0;
            for (int i = 0; i < N; i++) {
                for (int j = 0; j < M; j++) {
                    visited[i][j] =false;
                }
            }
            return;
        }

        for (int i = 0; i < N; i++) {
            for (int j = 0; j < M; j++) {
                if (a[i][j]== 0) {
                    // 벽을 세우기
                    a[i][j] =1;
                    go(x+1);
                    a[i][j] =0;
                }
            }
        }

    }


    public static void main(String[] args) {
        input();
        go(0);

        System.out.println(max);
    }


    static class FastReader {
        BufferedReader br;
        StringTokenizer st;

        public FastReader() {
            br = new BufferedReader(new InputStreamReader(System.in));
        }

        public FastReader(String s) throws FileNotFoundException {
            br = new BufferedReader(new FileReader(new File(s)));
        }

        String next() {
            while (st == null || !st.hasMoreElements()) {
                try {
                    st = new StringTokenizer(br.readLine());
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            return st.nextToken();
        }

        int nextInt() {
            return Integer.parseInt(next());
        }

        long nextLong() {
            return Long.parseLong(next());
        }

        double nextDouble() {
            return Double.parseDouble(next());
        }

        String nextLine() {
            String str = "";
            try {
                str = br.readLine();
            } catch (IOException e) {
                e.printStackTrace();
            }
            return str;
        }
    }
}

```
