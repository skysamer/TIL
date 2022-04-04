## 💡 일정 재구성
[from, to]로 구성된 항공권 목록을 이용해 JFK에서 출발하는 여행 일정을 구성하는 문제다.
여러 일정이 있는 경우 사전 어휘순으로 방문한다.

Example 1:

Input: tickets = [["MUC","LHR"],["JFK","MUC"],["SFO","SJC"],["LHR","SFO"]]
Output: ["JFK","MUC","LHR","SFO","SJC"]

Example 2:

Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]

Example 3:

Input: tickets = [["JFK","SFO"],["JFK","ATL"],["SFO","ATL"],["ATL","JFK"],["ATL","SFO"]]
Output: ["JFK","ATL","JFK","SFO","ATL","SFO"]
Explanation: Another possible reconstruction is ["JFK","SFO","ATL","JFK","ATL","SFO"] but it is larger in lexical order.

dfs와 우선순위큐 객체를 활용하여 문제를 해결했다.
~~~java
public class Solution {
    public List<String> findItinerary(List<List<String>> tickets) {
        /**
         * key는 출발지, value는 출발지와 매핑되는 목적지 list
         * PriorityQueue를 통해 출발지가 같은 목적지를 list로 묶어 사전순으로 정렬
         * */
        Map<String, PriorityQueue<String>> ticketGroup=new HashMap<>();

        for(List<String> ticket : tickets){
            PriorityQueue<String> priorityQueue=ticketGroup.getOrDefault(ticket.get(0), new PriorityQueue<String>());
            priorityQueue.offer(ticket.get(1));

            /**
             * 출발지가 같은 목적지 list로 update되어 출발지 key의 value가 갱신됨(중복 key를 허용하지 않기 때문)
             * */
            ticketGroup.put(ticket.get(0), priorityQueue);
        }

        return dfs("JFK", new LinkedList<>(), ticketGroup);
    }

    public List<String> dfs(String currentStop, LinkedList<String> itinerary, Map<String, PriorityQueue<String>> possibleWays){
        PriorityQueue<String> destination=possibleWays.getOrDefault(currentStop, new PriorityQueue<String>());

        /**
         * 출발지가 같은 목적지 list에서 사전순에 우위가 있는 posibleWays에서 제거하면서 목적지를 출발지로 하여 재귀 호출
         * */
        while(!destination.isEmpty()){
            dfs(destination.poll(), itinerary, possibleWays);
        }

        /**
         * 재귀를 빠져나오면서, 도착지 -> 경유지 -> 출발지 순으로 itinerary 첫번째 인덱스에 삽입
         * */
        itinerary.offerFirst(currentStop);
        return itinerary;
    }
}
~~~

-----
</br>
