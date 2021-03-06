# DBMS

**DB 정보를 검색하고 저장하는 데 사용하기에 편리하고 효율적인 환경 제공 위한 시스템**
<br/>

DB는 데이터그자체, DBMS는 데이터를 포함(DB)하며 관리(control program) ⇒ `DBMS = DataBase + Control Program` 

<br/>

### **DBMS가 있기 전 존재했던 문제점들**   (== DMBS의 장점이자 필요성, 솔루션, 특징)

1. Data redundancy and inconsistency (데이터 중복과 불일치)
    데이터가 여러 파일형식으로 저장돼서 다른 파일에 데이터가 중복
        
2. 데이터를 접근하기 어려움
    데이터를 접근하려면 프로그램을 작성해야되므로 접근할때마다 작성해야하는 어려움
        
3. Data isolation (데이터 고립)        
    다양한 파일과 형식이 존재하기때문에 그 형식에 맞춰져있으므로 고립
        
4. Integrity problems (무결성 문제) (Integrity : 데이터베이스에 저장된 데이터의 정확성과 일관성)        
    데이터들의 제한조건(잔고가 0보다 커야한다)이 존재하는데 이 조건은 코드속에 묻혀있어 명시적이지 않으며 조건이 변하거나 관리할 때 MS이 없어서 관리가 힘듦
        
5. Atomicity of updates (일부분만 업데이트)        
    부분적인 update로 인해 데이터베이스가 일관성을 유지하지 못한 상태로 남아있는 가능성
        
    ex) 계좌에서 이체는 **완전히 이뤄지던가 아예 안 일어나야함** → 부분적 update로 인해 한쪽은 돈을 보냈지만 다른 한쪽이 돈을 못받으면 안됨    ⇒ roll-back 후 문제 해결해 다시 수행
        
6. Concurrent access by multiple users (여러 사용자들의 동시접근)        
    성능을 위해 동시 접근이 필요하지만, 제어되지 않는 동시접근은 불일치성을 야기시킴
        
    ex) 두 사람이 잔액(100)을 읽고 동시에 50을 인출한다.
        
7. Security Problems (보안 문제)        
    사용자에게 접근을 제공하기 어려움.   모두에게 접근을 허용하게 하면 안됨(보안)