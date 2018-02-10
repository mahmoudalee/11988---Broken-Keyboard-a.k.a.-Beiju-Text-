# 11988---Broken-Keyboard-a.k.a.-Beiju-Text-

#include <iostream>

#include <queue>
 
using namespace std;
 
int main()
{

  deque<string> q;
  
	string broken, w = "", f = "";
  
	while (cin >> broken)
	{
		w = "", f = "";
		bool flag = 0;
 
		for (int i = 0; i < broken.size(); i++)
		{
			if (broken[i] != '[')
			{
				if (flag && broken[i] != ']')
				{
					f += broken[i];
					continue;
				}
				else if (broken[i] == ']')
				{
					q.push_front(f);
					flag = 0;
					f = "";
					q.push_back(w);
					w = "";
					continue;
				}
				else 
					w += broken[i];
			}
			else
			{
				q.push_front(f);
				f = "";
				q.push_back(w);
				w = "";
				flag = 1;
			}
		}
		q.push_back(w);
		q.push_front(f);
		while (!q.empty())
		{
			cout << q.front();
			q.pop_front();
		}
		cout << endl;
	}
	return 0;
}
