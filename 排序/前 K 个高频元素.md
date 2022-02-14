[347. Top K Frequent Elements](https://leetcode-cn.com/problems/top-k-frequent-elements/)

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        unordered_map<int,int> umap;
        for(int i=0;i<nums.size();i++){
            umap[nums[i]]++;
        }
        priority_queue <pair<int,int>> pq;
        for(auto p:umap){
            pq.push(pair<int,int>(-p.second,p.first));
            if(pq.size()>k){
                pq.pop();
            }
        }
        vector<int> ret;
        for(int i=0;i<k;i++){
            ret.push_back(pq.top().second);
            pq.pop();
        }
        return ret;
    }
};
```
