/class Solution {
public:
    // vector<vector<int>> threeSum(vector<int>& nums) {
    //     int n = nums.size();

    //     vector<vector<int>> ans;
    //     if(n<3){
    //         return ans;
    //     }

       

    //     sort(nums.begin(), nums.end());

    //     set<vector<int>> s;

    //     for(int i =0; i<n; i++){
            
    //         int j = i+1; int k =n-1;
        

    //         while(j<k){

               
    //             if((nums[i]+ nums[j]+ nums[k]) == 0){
    //                 ans.push_back({nums[i], nums[j], nums[k]});
    //                 j++;
    //                 k--;
    //             }

    //             if((nums[i]+ nums[j]+ nums[k]) > 0){
                    
    //                 k--;
    //             }

    //             if((nums[i]+ nums[j]+ nums[k]) < 0){
                    
    //                 j++;
    //             }


    //         }
            
    //     }

    //      for(auto triplets :s){
    //         ans.push_back(triplets);
                                                                
    //      }
    //      return ans;

    vector<vector<int>> threeSum(vector<int>& nums) {
        int n=nums.size();
        vector<vector<int>>result;
        sort(nums.begin(), nums.end());

        for(int i=0; i<n; i++)
        {
            if(i>0 && nums[i]==nums[i-1])
            {
                continue;
            }
            int j=i+1;
            int k=n-1;
            
            while(j<k)
            {
                int total=nums[i]+nums[j]+nums[k];
                if(total>0)
                {
                    k--;
                }
                else if(total<0)
                {
                    j++;
                }
                else{
                    result.push_back({nums[i], nums[j], nums[k]});
                    j++;
                   
                    while(nums[j]==nums[j-1] && j<k)
                    {
                        j++;
                    }
                }
            }
        }
        return result;

    }
};
