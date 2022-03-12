## 💡 섬의 개수
1을 육지로, 0을 물로 가정한 2D 그리드 맵이 주어졌을때, 섬의 개수를 구하는 문제다.
(연결되어 있는 1의 덩어리 개수를 구해야 한다)

Example 1:

Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1

Example 2:

Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3

기본적으로 재귀를 활용한 재귀호출로 문제를 해결했다.

배열을 순회하면서 지점이 육지일 경우,
해당지점을 기준으로 동서남북으로 순회하면서 육지지점을 탐색한다.

더이상 붙어있는 육지가 없을 경우 재귀호출을 마치고 섬의 개수를 카운팅하고 다시 배열을 순회한다.
~~~java
public class NumberOfIsland {

	int[][] changePos={{1, 0}, {-1, 0}, {0, 1}, {0, -1}}; /*grid의 한 지점에서 동서남북으로 순회할 수 있도록 구성한 임의의 배열*/
	int row;
	int column;

	public void DFS(int r, int c, boolean[][] visited, char[][] grid){
		visited[r][c]=true;
		
		int nextRow;
		int nextColumn;
		
		for(int i=0; i<changePos.length; i++){
			nextRow=r+changePos[i][0];
			nextColumn=c+changePos[i][1];
			
			/*nextRow, nextColumn이 grid 배열 범위에 포함되지 않는 경우 row와 column의 다음값 다시 설정*/
			if(nextRow<0 || row<=nextRow || nextColumn<0 || column<=nextColumn){
				continue;
			}
			
			/**
			 * 도착한 배열의 지점이 육지고, 방문하지 않은 곳인 경우 재귀 호출
			 * */
			if(!visited[nextRow][nextColumn] && grid[nextRow][nextColumn]=='1'){
				DFS(nextRow, nextColumn, visited, grid);
			}
		}

	}

	public int numIslands(char[][] grid) {
		row=grid.length;
		column=grid[0].length;
		
		boolean[][] visited=new boolean[row][column];
		int countIsland=0;
		
		/*grid 배열 전체 순회*/
		for(int r=0; r<row; r++){
			for(int c=0; c<column; c++){
				
				/**
				 * 방문하지 않은 곳이 육지인 경우
				 * 이 지점이 육지인 경우 주변에 탐색되는 모든 육지를 재귀 호출을 통해 순회한 다음
				 * 다시 이 반복문으로 돌아와 섬의 개수를 카운팅하고 
				 * 다시 원 배열을 순회한다.
				 * 섬이 하나인 경우 재귀가 한 번 호출되고 빠져 나온 이후에는 다시 재귀가 호출되지 않고 배열을 전부 순회한 뒤 메서드가 종료된다.
				 * 즉, 재귀 호출 횟수 = 섬의 개수
				 * */
				if(!visited[r][c] && grid[r][c]=='1'){
					DFS(r, c, visited, grid);
					countIsland++;
				}
			}
		}

		return countIsland;
	}

}

~~~

-----
</br>
