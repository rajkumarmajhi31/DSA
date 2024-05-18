int i = 0, j = 0, ans = 0;
for (; j < N; ++j) {
    // CODE: use A[j] to update state which might make the window invalid
    for (; invalid(); ++i) { // when invalid, keep shrinking the left edge until it's valid again
        // CODE: update state using A[i]
    }
    ans = max(ans, j - i + 1); // the window [i, j] is the maximum window we've found thus far
}
return ans;

![image](https://github.com/rajkumarmajhi31/DSA/assets/118106939/47e406ab-ad7e-41ad-94d0-bcd65c7fb13c)
// This is one of the pattern of DSA asked in interviews
