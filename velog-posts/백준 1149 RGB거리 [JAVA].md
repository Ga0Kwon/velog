<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/a4187eab-bbb4-4280-843f-452b6aef7f38/image.png" /></p>
<blockquote>
<h2 id="문제-해석">문제 해석</h2>
</blockquote>
<ul>
<li>문제를 한마디로 요약하면 &quot;<span style="color: green;"><strong>서로 같은 색이 인접하지 않게 최소 비용으로 색칠</strong></span>하기&quot; 이다.</li>
<li>그렇기 때문에 전에 사용하는 색 중 가장 작은 색을 누적더하기하여 최종으로 N-1(배열이기 때문에)의 최소비용을 구하면 된다. (누적 더하기를 했기 때문에)</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/5906e8ba-e480-4c7e-a915-3a3db2d877f4/image.png" /></p>
<blockquote>
<h2 id="코드">코드</h2>
</blockquote>


<pre><code class="language-java">import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import java.util.StringTokenizer;

public class Main {
    static int[][] homeColor;

    static int count;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        homeColor = new int[N][3];

        StringTokenizer st;

        for(int i = 0; i &lt; N; i++){ //배열 초기회
            st = new StringTokenizer(br.readLine());
            for(int j = 0; j &lt; 3; j++){
                homeColor[i][j] = Integer.parseInt(st.nextToken());
            }
        }

        br.close();


        //최솟값 찾기 (1부터 N-1인 이유는 0번째는 어차피 그 비용이기도 하고, N-1은 배열은 0인덱스이기 때문)
        for(int i = 1; i &lt; N; i++){ //서로 다른 색(직전의)의 비용의 최솟값을 누적더하기
            homeColor[i][0] += Math.min(homeColor[i-1][1], homeColor[i-1][2]);
            homeColor[i][1] += Math.min(homeColor[i-1][0], homeColor[i-1][2]);
            homeColor[i][2] += Math.min(homeColor[i-1][1], homeColor[i-1][0]);
        }

        System.out.println(Math.min(homeColor[N-1][0], Math.min(homeColor[N-1][1], homeColor[N-1][2])));
    }
}</code></pre>


<blockquote>
<h2 id="결과">결과</h2>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/6d531aa6-bc5e-4dda-878d-eb79a3f88ced/image.png" /></p>
<blockquote>
<h2 id="느낀-점">느낀 점</h2>
</blockquote>
<ul>
<li>처음에 어떻게 해야할지 생각이 안나서 막막했지만 여러 분들의 코드를 봐보니 그래도 바로 이해할 수 있었다.</li>
</ul>
