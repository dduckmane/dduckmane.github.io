---
layout: single
title:  "[코딩테스트] 백준 1987번"
categories: CodingTest
tag: [개념]

author_profile: false
sidebar:
    nav: "counts"
---

[유형]
- 그래프 이론

[특징]
- 보통 dfs 처럼 visit check를 하게 된다면 모든 경로를 한번 씩만 이동
- 하지만 이 문제는 모든 경로를 다 가보아야 한다.
- 그러기에 visit check 을 해주고 풀어주는 과정이 필요

```
import java.io.*;
import java.util.StringTokenizer;

public class Main {
    static FastReader scan = new FastReader();
    static StringBuilder sb = new StringBuilder();


    static int R;
    static int C;
    static String[] a;
    static int[][] dir = new int[][] {{1 , 0}, {-1 , 0}, {0 , 1}, {0 , -1}};
    static boolean[][] visit;
    static int max = Integer.MIN_VALUE;


    static void input() {
        R = scan.nextInt();
        C = scan.nextInt();

        a = new String[R];
        visit = new boolean[R][C];

        for (int i = 0; i < R; i++) {
            a[i] = scan.next();
        }
    }

    static void dfs(int x, int y, String str, int res) {
        max = Math.max(max , res);

        for (int i = 0; i < 4; i++) {
            int dx = x + dir[i][0];
            int dy = y + dir[i][1];

            if (dx < 0 || dx >= R || dy < 0 || dy >= C) continue;
            if (visit[dx][dy]) continue;
            if (str.contains(String.valueOf(a[dx].charAt(dy)))) continue;

            // visit
            visit[dx][dy] = true;
            dfs(dx , dy, str.concat(String.valueOf(a[dx].charAt(dy))), res + 1);
            // 해제
            visit[dx][dy] = false;
        }
    }

    
    public static void main(String[] args) {
        input();
        dfs(0 , 0, String.valueOf(a[0].charAt(0)), 1);
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
