1. This is student portal backup

// Now i add a code.

#include<bits/stdc++.h>
using namespace std;

#define lt long int
#define ll long long int
#define cn cin
#define co cout
#define nl endl
#define vec vector
#define pb push_back
#define all(v) v.begin(), v.end()
#define loop(i,n) for(int i=0; i<(n); i++)

class Node{
public:
	int data;
	Node* next;

	Node(int val){
		data = val;
		next = NULL;
	}
};

class List{
	Node* head;
	Node* tail;

public:
	List(){
		head = tail = NULL;
	}

	void push_back(int val){
		Node* newNode = new Node(val);
		if(head == NULL){
			head = tail = newNode;
			return;
		}
		else{
			tail->next = newNode;
			tail = newNode;
		}
	}

	void split(Node*& front, Node*& back){

		if(head == NULL || head->next == NULL){
			front = head;
			back = NULL;
			return;
		}

		Node* slw = head;
		Node* fst = head->next;;

		while(fst != NULL){
			fst = fst->next;
			if(fst != NULL){
				slw = slw->next;
				fst = fst->next;
			}
		}


		front = head;
		back = slw->next;
		slw->next = NULL;
	}

	void print(){
		Node* tmp = head;
		while(tmp != NULL){
			co<<tmp->data<<" ";
			tmp = tmp->next;
		}
		co<<nl;
	}
};

void printlst(Node* head){
	Node* tmp = head;
	while(tmp != NULL){
		co<<tmp->data<<" ";
		tmp = tmp->next;
	}
	co<<nl;
}

void solve(){
	List lnk_lst;
	for(int i=1;i<=7;i++){
		lnk_lst.push_back(i);
	}

	lnk_lst.print();

	Node* front = NULL;
	Node* back = NULL;

	lnk_lst.split(front, back);

	co<<"The front list : "<<nl;
	printlst(front);

	co<<nl<<nl;

	co<<"The back list : "<<nl;
	printlst(back);
}


int main(){
	ios::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);

    solve();
}
