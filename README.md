# Binary-Search-Tree-Complete#include<conio.h>
#include<iostream>
#include<queue>
using namespace std;
struct BSTnode
{
    int data;
    BSTnode *left;
    BSTnode *right;
};
BSTnode* newnode(int data)
{
    BSTnode *root=new BSTnode();
    root->data=data;
    root->left=root->right=NULL;
    return root;
}
BSTnode* insert(BSTnode* root,int data)
{
  if(root==NULL)
        root=newnode(data);
        else if(data<root->data)
        {
         root->left=insert(root->left,data);
        }
        else
        {
            root->right=insert(root->right,data);
        }
        return root;
}
bool search(BSTnode* root,int item)
{
    if(root==NULL)
        return false;
    else if(root->data==item)
        return true;
    else if (root->data>=item)
        return search(root->left,item);
    else
        return search(root->right,item);
    }
 int max(BSTnode* root)
 {
     if(root==NULL)
        return -1;
     else if(root->right==NULL)
            return root->data;
     else
        return max(root->right);
 }
 int min(BSTnode *root)
 {
     if(root==NULL)
        return -1;
     else if(root->left==NULL)
        return root->data;
     else
        return min(root->left);
 }
 // Function to print Nodes in a binary tree in Level order
void LevelOrder(BSTnode *root) {
	if(root == NULL) return;
	queue<BSTnode*> Q;
	Q.push(root);
	//while there is at least one discovered node
	while(!Q.empty()) {
		BSTnode* current = Q.front();
		Q.pop(); // removing the element at front
		cout<<current->data<<" ";
		if(current->left != NULL) Q.push(current->left);
		if(current->right != NULL) Q.push(current->right);
	}
}
void Preorder(BSTnode* root)
{
  if(root==NULL)
        return;
  else
  {
      cout<<root->data<<" ";
      Preorder(root->left);
      Preorder(root->right);
  }
}
void Inorder(BSTnode* root)
{
  if(root==NULL)
  return;
  else
  {
      Inorder(root->left);
      cout<<root->data<<" ";
      Inorder(root->right);
  }
}
void Postorder(BSTnode *root)
{
    if(root==NULL)
        return;
    else
    {
     Postorder(root->left);
     Postorder(root->right);
     cout<<root->data<<" ";
    }
}
int main()
{
    BSTnode *root=NULL;
    int number,item,maximum,minimum,s;
    while(1)
    {
        cout<<endl<<"Press 1 for Insert: ";
        cout<<endl<<"Press 2 for Search: ";
        cout<<endl<<"Press 3 for Maximum: ";
        cout<<endl<<"Press 4 for Minimum: ";
        cout<<endl<<"Press 5 for Level Order Traversal: ";
        cout<<endl<<"Press 6 for Pre Order Traversal: ";
        cout<<endl<<"Press 7 for In Order Traversal: ";
        cout<<endl<<"Press 8 for Post Order Traversal: ";
        cout<<endl<<"Press 9 for Exit: ";
        cout<<endl<<"Enter your choice: ";
        cin>>s;
        switch(s)
        {
            case 1:cout<<endl<<"Enter a number: ";
                   cin>>number;
                   root=insert(root,number);
                break;
            case 2: cout<<endl<<"Enter the number :";
                    cin>>item;
                    if(search(root,item)==1)
                        cout<<endl<<"Number Found: ";
                    else
                        cout<<endl<<"Number Not Found: ";
                    break;
            case 3: maximum=max(root);
                    cout<<endl<<"Maximum Number is: "<<maximum;
                    break;
            case 4: minimum=min(root);
                    cout<<endl<<"Minimum Number is: "<<minimum;
                    break;
            case 5: LevelOrder(root);
                    break;
            case 6: Preorder(root);
                    break;
            case 7: Inorder(root);
                    break;
            case 8: Postorder(root);
                    break;
            case 9: exit(0);
                    break;
        }
    }
    getch();
}
