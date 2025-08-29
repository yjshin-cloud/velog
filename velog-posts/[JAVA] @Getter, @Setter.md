<h1 id="🧩-상황-이해부터">🧩 상황 이해부터</h1>
<p>자바(Java)라는 언어에서는 클래스(class) 안에 있는 데이터를 외부에서 바로 만지지 못하게 막아둡니다.
대신 데이터를 읽거나 바꾸려면 <strong>특별한 문(메서드)</strong>를 열어서만 접근할 수 있어요.</p>
<p>예를 들어, 사람이름(name)을 저장하는 클래스를 만든다고 해봅시다.</p>
<h1 id="📄-gettersetter-없는-경우">📄 Getter/Setter 없는 경우</h1>
<p>public class Member {
    private String name;  // 이름(데이터)은 외부에서 직접 만질 수 없음
}</p>
<p>private라서 외부에서 name을 읽거나 바꿀 수 없음</p>
<p>그래서 전통적으로는 이렇게 Getter/Setter 메서드를 만들어줘야 했습니다:</p>
<pre><code class="language-code">public class Member {
    private String name;

    // Getter (읽는 메서드)
    public String getName() {
        return name;
    }

    // Setter (바꾸는 메서드)
    public void setName(String name) {
        this.name = name;
    }
}</code></pre>
<p>getName() → 이름 꺼내기</p>
<p>setName(&quot;kim&quot;) → 이름 바꾸기</p>
<p>⚡ Lombok @Getter, @Setter 사용</p>
<p>Lombok의 @Getter, @Setter를 쓰면 이렇게만 적어도:</p>
<pre><code>import lombok.Getter;
import lombok.Setter;

public class Member {
    @Getter @Setter
    private String name;
}</code></pre><p>👉 컴파일할 때 자동으로 위에 길게 쓴 getName() / setName() 메서드를 만들어 줍니다.</p>
<p>🎯 비전공자식 비유</p>
<p>데이터(name) = 금고 안에 든 돈</p>
<p>Getter/Setter 메서드 = 금고 열쇠 (열어서 확인하거나 돈 넣기)</p>
<p>Lombok의 @Getter/@Setter = 자동으로 열쇠를 만들어주는 기계
→ 일일이 열쇠(메서드)를 손으로 깎을 필요가 없음</p>
<p>🏢 현업에서는 어떻게 쓰일까?</p>
<p>장점</p>
<p>불필요하게 길고 반복적인 코드를 줄여서 가독성↑</p>
<p>유지보수도 쉬워짐 (“Getter/Setter 어디 있더라?” 찾을 필요 없음)</p>
<p>협업 시 팀원들도 “롬복 쓰네? Getter/Setter는 자동이구나” 하고 이해</p>
<p>주의점</p>
<p>무분별한 Setter 남발은 위험 ⚠️
→ 객체의 값이 아무 때나 막 바뀔 수 있음 → 버그 or 안정성↓
→ 현업에서는 불변객체(Setter 없는 클래스), 생성자 주입을 더 선호하는 경우 많음</p>
<p>그래서 실무에선 보통 @Getter만 쓰고, @Setter는 꼭 필요한 경우에만 제한적으로 붙입니다.</p>
<p>✅ 정리</p>
<p>@Getter: 필드 값을 꺼내는 메서드를 자동 생성</p>
<p>@Setter: 필드 값을 바꾸는 메서드를 자동 생성</p>
<p>롬복(Lombok): 자바에서 반복되는 코드(게터/세터/생성자 등)를 자동으로 만들어주는 편리한 도구</p>
<p>실무 사용법: Getter는 자주, Setter는 신중히 ✍️</p>
<h2 id="🔑-1-불변-객체immutable-object-스타일">🔑 1. 불변 객체(Immutable Object) 스타일</h2>
<pre><code>public class Member {
    private final String name;   // final → 한 번 세팅되면 바꿀 수 없음

    public Member(String name) { // 생성자로만 값 설정
        this.name = name;
    }

    public String getName() {    // 읽기 전용
        return name;
    }
}</code></pre><p>특징</p>
<p>name은 한 번 생성 시점에만 세팅되고, 이후에는 변경 불가</p>
<p>데이터 안정성 ↑ (중간에 값이 바뀌지 않아 예측 가능)</p>
<p>함수형/멀티스레드 환경에서 안전</p>
<h2 id="⚡-2-lombok-gettersetter-스타일">⚡ 2. Lombok Getter/Setter 스타일</h2>
<pre><code>import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
public class Member {
    private String name;  // setter로 언제든 변경 가능
}</code></pre><p>특징</p>
<p>getName(), setName() 자동 생성</p>
<p>코드 간결, 생산성 ↑</p>
<p>하지만 언제든 값 변경 가능 → 상태 추적 어려워질 수 있음</p>
<p>📊 3. Mermaid 시각화 – 객체 흐름 비교</p>
<pre><code class="language-mermaid">flowchart LR
    subgraph Immutable[&quot;불변 객체 (Immutable)&quot;]
        A1[Member 생성자 호출&lt;br/&gt;new Member(&quot;영준&quot;)] --&gt; B1[필드 name = &quot;영준&quot;]
        B1 --&gt; C1[getName()으로 읽기만 가능]
        C1 --&gt;|변경 불가| B1
    end

    subgraph Lombok[&quot;Lombok Getter/Setter&quot;]
        A2[Member 생성자 호출&lt;br/&gt;new Member()] --&gt; B2[name 필드 (null)]
        B2 --&gt; C2[setName(&quot;영준&quot;) → 값 변경]
        C2 --&gt; D2[getName() → &quot;영준&quot;]
        D2 --&gt; C2[setName(&quot;철수&quot;) → 또 변경]
    end</code></pre>
<p>🧭 현업에서의 사용 패턴</p>
<p>불변 객체 스타일</p>
<p>DTO, 엔티티 중에서도 &quot;절대 바뀌면 안 되는 값(예: ID, 생성일)&quot;에 활용</p>
<p>도메인 모델링 시 “불변성을 보장”하면 비즈니스 로직이 단순해짐</p>
<p>최근엔 JPA + 불변 엔티티 + Builder 패턴을 조합하는 경우도 많음</p>
<p>Lombok Getter/Setter 스타일</p>
<p>간단한 DTO, Request/Response 객체에 자주 사용</p>
<p>Setter는 테스트/데모 코드에서 편리</p>
<p>그러나 서비스 핵심 로직 객체에는 Setter를 최소화하는 추세</p>
<h2 id="✅-정리">✅ 정리:</h2>
<p>불변 객체: 안정성·예측 가능성 필요할 때</p>
<p>Lombok Getter/Setter: 개발 속도·간단한 데이터 전달에 유용</p>