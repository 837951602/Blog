[Moved from](https://github.com/837951602/Misc/blob/master/Algo/reversed_iterator.md)

    #include <set>
    #include <iostream>
    using std::set;
    using std::cout;
    
    int main() {
        std::set<int> values = {3,7,8,9,11,16,22};
        auto lit = values.rbegin();
        for (auto it = values.rbegin(); it != values.rend(); ++it) {
            if (*lit - *it == 1) {
                values.erase(*lit);
            }
            lit = it;
        }
        for (int x: values) {
            cout << x << '\n';
        }
    }

This code crashes. Not seen mentioned somewhere else. AI can't answer either.

This is a constructed example. I didn't really suffer it.
