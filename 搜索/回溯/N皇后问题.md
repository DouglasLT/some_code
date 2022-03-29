[51. N-Queens](https://leetcode-cn.com/problems/n-queens/)

```cpp
class Solution {
public:
    vector<vector<string>> solveNQueens(int n) {
        vector<string> board(n,string(n,'.'));
        vector<vector<string>> ret;
        backtrack(ret,board,0);
        return ret;
    }

    int isvalid(vector<string>& board,int row,int col){
        int n=board.size();
        for(int i=0;i<row;i++){
            if(board[i][col]=='Q'){
                return 0;
            }
        }

        for(int i=row-1,j=col-1;i>=0&&j>=0;i--,j--){
            if(board[i][j]=='Q'){
                return 0;
            }
        }

        for(int i=row-1,j=col+1;i>=0&&j<=n-1;i--,j++){
            if(board[i][j]=='Q'){
                return 0;
            }
        }
        return 1;
    }

    void backtrack(vector<vector<string>>& ret,vector<string>& board,int row){

        if(board.size()==row){
            ret.push_back(board);
            return ;
        }
        int n=board.size();
        for(int col=0;col<n;col++){
            if(!isvalid(board,row,col)){
                continue;
            }
            board[row][col]='Q';
            backtrack(ret,board,row+1);
            board[row][col]='.';
        }
    }
    
};
```
