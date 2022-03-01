## 💡 해시맵 디자인
해시맵을 구현하는 문제다.

값을 집어넣는 put(), key에 매핑되는 value를 리턴하는 get(), key값을 가지고 있는 객체를 제거하는 remove() 메서드를 구현한다.
key와 value값의 범위는 0 ~ 1,000,000이다.

key와 매핑되는 value를 저장하고 있는 bucket객체를 생성한다.
해시 충돌이 발생할 경우, 개별체이닝 방식을 구현하여 해결했다.

~~~java
package smlab;

public class MyHashMap {
	
	static final int BUCKET_CAPACITY=100; /*100개 씩 bucket별로 관리*/
	static Bucket[] buckets;
	
	/*value 저장소 : key와 매핑되는 value값들을 저장하고 있는 저장소다.*/
	class Bucket{
		Node node;
		
		public Bucket(Node node){
			this.node=node;
		}
	}
	
	/**
	 *key, value쌍을 저장하고 있는 객체
	 *next변수값을 통해 다른 node와 연결 */
	class Node{
		int key;
		int value;
		Node next;
		
		public Node(int key, int value, Node next){
			this.key=key;
			this.value=value;
			this.next=next;
		}
	}
	
	/*bucket의 메모리 공간 초기화*/
	public MyHashMap() {
        buckets=new Bucket[10001];
    }
    
    public void put(int key, int value) {
        int index=key / BUCKET_CAPACITY; /*각 bucket당 100개씩 노드를 관리하기 때문에 버킷 용량으로 key값을 나누어 인덱스 설정*/

        /*해당 인덱스가 없을 경우 인자의 key,value를 갖는 bucket과 node 객체 생성*/
        if(buckets[index]==null){
        	buckets[index]=new Bucket(new Node(key, value, null));
        }
        
        /**인덱스가 존재할 경우
         * key가 중복일경우 value만 업데이트하여 저장
         * 해당 key가 bucket node에 존재하지 않을 경우 key,value 인자값을 갖는 node객체 생성 */
        else{
        	Node node=buckets[index].node;
        	
        	while(node!=null){
        		if(node.key==key){
        			node.value=value;
        			return;
        		}
        		
        		if(node.next==null){
        			node.next=new Node(key, value, null);
        			return;
        		}
        		
        		node=node.next;
        	}
        }
    }
    
    /*key 인자값이 존재하지 않을 경우 -1 리턴*/
    public int get(int key) {
        int index=key / BUCKET_CAPACITY;
        
        if(buckets[index]==null){
        	return -1;
        }
        
        /*node 객체의 연결리스트를 순회하면서 해당 key에 매핑되는 value를 리턴*/
        else{
        	Node node=buckets[index].node;
        	
        	while(node!=null){
        		if(node.key==key){
        			return node.value;
        		}
        		node=node.next;
        	}
        	
        	return -1;
        }
    }
    
    public void remove(int key) {
        int index=key/BUCKET_CAPACITY;
        
        if(buckets[index]==null){
        	return;
        }
        else{
        	Node node=buckets[index].node;
        	Node prev=null;
        	
        	while(node!=null){
        		
        		if(node.key==key){
        			
        			if(prev==null){
        				buckets[index].node=node.next;
        				
        				if(node.next==null){
        					buckets[index]=null;
        				}
        				return;
        			}
        			else{
        				prev.next=node.next;
        				return;
        			}
        			
        		}
        		else{
        			prev=node;
        			node=node.next;
        		}
        		
        	}
        }
    }
    
}

~~~

-----
</br>
