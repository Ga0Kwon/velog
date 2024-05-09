<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/c90c8520-3bcb-4f11-810c-8d8e3e03df42/image.png" /></p>
<blockquote>
<h2 id="문제-해석">문제 해석</h2>
</blockquote>
<ul>
<li>첫째 줄에 사람의 수(<span style="color: green;"><strong>N</strong></span>)을 입력 받고, N번 만큼 각 사람이 돈을 인출하는 데 걸리는 <span><strong>시간 P¡</strong></span> 을 입력받는다.</li>
<li>모두 입력받았으면 사람의 배치를 다르게 하여 <span style="color: green;"><strong>최소 필요 시간</strong></span>을 구하면 된다.
<img alt="" src="https://velog.velcdn.com/images/gayeong39/post/cb998754-fadd-400e-8623-6398f1c13abd/image.png" /></li>
</ul>
<blockquote>
<h2 id="코드">코드</h2>
</blockquote>
<pre><code class="language-java">import java.io.*;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        int N = Integer.parseInt(br.readLine()); //총 사람 수

        int[] schedule = new int[N]; // 사람 횟수

        st = new StringTokenizer(br.readLine());

        for(int i = 0; i &lt; N; i++){
            schedule[i] =  Integer.parseInt(st.nextToken()); //시작 시간
        }

        br.close();

        Arrays.sort(schedule); //배열 정렬 (적은 시간 -&gt; 큰 시간)

        int[] preSum = new int[N]; //시간을 누적합해서 저장할 배열

        preSum[0] = schedule[0];
        int result = preSum[0]; //총 최소 시간을 넣는 배열

        for(int i = 1; i &lt; schedule.length; i++){
            preSum[i] = preSum[i-1] + schedule[i]; //누적합
            result += preSum[i]; //총 최소 시간
        }

        System.out.println(result);

    }
}</code></pre>
<blockquote>
<h2 id="결과">결과</h2>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gayeong39/post/5ba8ac71-5ef5-4cfe-8081-e0ada96de62e/image.png" /></p>
<blockquote>
<h2 id="느낀-점">느낀 점</h2>
</blockquote>
<p>이 문제는 크게 어려움없이 금방 풀 수 있는 문제였다. 문제를 읽다보니 자연스럽게 정렬을 해야겠다는 생각이 들었고, 무작정 더하는 것보다 누적합이 더 효율적일 것 같아서 딱딱 그냥 풀 수 있는 문제였다.</p>