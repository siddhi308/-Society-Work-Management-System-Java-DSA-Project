# -Society-Work-Management-System-Java-DSA-Project
 We have created a management system for society work where this is accessible for 4  types of persons: Admin (Secretary) , Society Members , Other than Society Member  ,Helper .
 
# 🏡 Society Management System - Java DSA Project

## 📌 Overview

This is a **Java-based console application** that manages daily tasks of a residential society. The application is built using **core Java concepts and data structures** like Binary Search Trees and Linked Lists. It covers management of society members, maintenance fees, helper staff, and hall booking system.

---

## 🧰 Modules & Features

### 1. 📅 Society Member Management (Binary Search Tree)

* Add, Update, Delete, and Search member records
* Fields include: Name, Flat Number, Flat Status (Owner/Tenant), Life Status (Family/Bachelor), Phone Number, Maintenance Due
* Flat numbers are stored in a **BST** to ensure fast search and ordering

### 2. 📞 Phone Directory & Sorting

* Display all member phone numbers
* Search member by flat number or phone number
* Sort members by:

  * Phone number
  * Name (alphabetically)

### 3. 🧱 Maintenance Fee Tracker

* Every flat pays ₹2500 every 6 months
* System tracks payments, dues, or overpayments
* Output displayed in readable format (Paid / Due)

### 4. 🏢 Hall Booking System (Doubly Linked List)

* Book society hall (2 halls available: 100 and 400 capacity)
* Validate and prevent duplicate bookings on the same date
* Store and display bookings using **doubly linked list**

### 5. 💼 Helper Staff Management (BST)

* Manage data for helpers: Watchman, Housekeeper, Gardner, etc.
* Store helper name, ID, area of work, phone number, and attendance status
* Mark attendance ("present") by helper login

### 6. 🔐 Role-Based Access System

| Role           | Password    | Permissions                                       |
| -------------- | ----------- | ------------------------------------------------- |
| Admin          | `ssva`      | Full access to member, helper, hall & maintenance |
| Society Member | `dream@123` | Can view, search, pay maintenance, book halls     |
| Helper         | `vssa`      | Can mark themselves present                       |
| Visitor        | None        | Can book and view hall bookings                   |

---

## 🔧 Technologies Used

* Java (Core)
* OOP: Classes, Objects, Encapsulation
* Data Structures: Binary Search Tree, Linked List, Stack
* Console Input via Scanner

---

## 📊 Sample Execution Flow

```bash
1) Admin Login
2) Add Member: Sakshi Manoj Deshmukh, Flat #7
3) Pay Maintenance: ₹2500
4) Book Hall #1 for 12/1/2023
5) Add Helper: Vishal (Housekeeper, ID: 1)
6) Display Members & Bookings
```

---

## 📁 Project Structure

* `SocietyWork.java` - Main driver class
* `BinarySearchTree.java` - Member management logic
* `BookHall1.java` - Hall booking module
* `BST.java` - Helper staff management
* `Node.java`, `Node1.java`, `Hall1.java` - Data entity models

---

## 🚀 How to Run

1. Compile:

```bash
javac SocietyWork.java
```

2. Run:

```bash
java SocietyWork
```

---

## 📝 Author

* Developed as part of a Java DSA academic project to demonstrate real-world application of data structures and object-oriented programming.



   ## CODE ;
   
import java.util.*; 
class Node{ 
    Node left, right,left1,left2,right1,right2; 
    String Name,flatstatus,lifestatus,TelephoneNo; 
    int flatno; 
    double totalMain; 
    Node next; 
     
    Node(String Name, String flatstatus,String lifestatus,int flatno,String TelephoneNo,double 
totalmain ){ 
        left = right = null; 
       this.Name=Name; 
       this.flatstatus=flatstatus; 
       this.lifestatus=lifestatus; 
       this.flatno=flatno; 
       this.TelephoneNo=TelephoneNo; 
       this.totalMain=2500.0; 
       next=null; 
    } 
 
     
    void display(){ 
      
      System.out.printf("%35s %20d %23s %20s %23s %16s 
",this.Name,this.flatno,this.flatstatus,this.lifestatus,this.TelephoneNo,this.totalMain+"\n"); 
      
    } 
    void displayno(){ 
      
      System.out.printf("%35s %20d %23s ",this.Name,this.flatno,this.TelephoneNo+"\n"); 
        
           } 
    void displaystatus(){ 
       
      System.out.printf("%35s %20d %23s %20s 
",this.Name,this.flatno,this.flatstatus,this.lifestatus+"\n"); 
      
    } 
    void displaymain(){ 
     if(this.totalMain==0) { 
      
        System.out.printf("%14d %20s",this.flatno,"paid\n"); 
        
     } 
     else if(this.totalMain>0) { 
            
       System.out.printf("%14d %17s %1s",this.flatno,"due:",this.totalMain); 
       
     } 
     else if(this.totalMain<0) { 
       
       System.out.printf("%14d %20s",this.flatno,"paid\n"); 
 
       
     } 
     else { 
      return; 
     } 
           } 
 
} 
 
class BinarySearchTree{ 
 
    Scanner sc = new Scanner(System.in); 
    Node root, root1,head, tail, root2;   
    int count=0; 
     
      
    BinarySearchTree(){                     
        root = null;  
          
    } 
    Stack < Node > q = new Stack <> (); 
     
     
    void create(){ 
      
      String Name,flatstatus,lifestatus,TelephoneNo; 
      int flatno; 
      float totalMain; 
        int ch=0; 
        do{ 
         String Namef,Namem,Namel; 
        
          System.out.println("Enter Flat number: "); 
             flatno = sc.nextInt(); 
             Node ptr1=root; 
              
      
     while(ptr1!=null) { 
      if(flatno==ptr1.flatno) { 
       System.out.println("these flat number is already 
present in record"); 
       return; 
      } 
     
       else if(flatno<ptr1.flatno){         
                   ptr1 = ptr1.left;                    
               } 
               else{ 
                   ptr1 = ptr1.right;                  
               }  
        
       
       
     } 
     
      
         System.out.println("Name"); 
            System.out.println("Enter first Name: "); 
            Namef = sc.next(); 
            System.out.println("Enter Middle Name: "); 
            Namem = sc.next(); 
            System.out.println("Enter last Name: "); 
            Namel = sc.next(); 
            Name=Namef+" "+Namem+" "+Namel; 
 
                     do { 
            System.out.println("Enter are you owner or tenant: "); 
               flatstatus = sc.next(); 
          if(flatstatus.equalsIgnoreCase("owner") || flatstatus.equalsIgnoreCase("tenant")) { 
               break; 
          } 
          else { 
               System.out.println("Enter correct one"); 
                
          } 
          }while((flatstatus.equalsIgnoreCase("owner") || flatstatus.equalsIgnoreCase("tenant")!=true)); 
           
             
            do { 
             System.out.println("Enter are you family or bachelor: "); 
                lifestatus = sc.next(); 
           if(lifestatus.equalsIgnoreCase("family") || lifestatus.equalsIgnoreCase("bachelor")) { 
                break; 
           } 
           else { 
                System.out.println("Enter correct one"); 
                 
           } 
           }while((lifestatus.equalsIgnoreCase("family") || 
lifestatus.equalsIgnoreCase("bachelor")!=true)); 
             
                        totalMain=2500; 
          do { 
            System.out.println("Enter phone number: "); 
            TelephoneNo = sc.next(); 
            
            if(TelephoneNo.length()==10) { 
            Node temp = new Node(Name, flatstatus,lifestatus,flatno,TelephoneNo,totalMain); 
             
            if(root == null){       
                root = temp; 
                count++; 
            } 
            else{ 
                Node ptr = root; 
                while(ptr != null){ 
 
                    if(temp.flatno<ptr.flatno){ 
                        if (ptr.left == null){ 
                            ptr.left = temp; 
                            count++; 
                            break; 
                        } 
                        else{ 
                            ptr = ptr.left; 
                        } 
                    } 
                    else if(temp.flatno>ptr.flatno){ 
                        if (ptr.right == null){ 
                            ptr.right = temp; 
                            count++; 
                            break; 
                        } 
                        else{ 
                            ptr = ptr.right; 
                        } 
                    } 
                    else{ 
                        System.out.println("Already present"); 
                        break; 
                    } 
                } 
            } 
            System.out.println("*******Record stored succesfully*******"); 
        } 
           else { 
             System.out.println("Enter valid phone number"); 
            } 
            }while(TelephoneNo.length()!=10); 
            System.out.print("\nDo you want to add more Member's information ?\nPress '1' to 
continue\nPress '0' to exit :"); 
    ch = sc.nextInt(); 
   System.out.println(""); 
       
  } while (ch != 0); 
        
       } 
     
     
  
    public void displayinfo(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
       System.out.printf("%30s %30s %20s %20s %20s %20s","Name","Flat 
Number","Flatstatus","Lifestatus","Phone number","MAintainence\n"); 
     displayinfo(this.root); 
     } 
    } 
 
    private void displayinfo(Node node){ 
      
        if (node != null){ 
         displayinfo(node.left); 
            node.display(); 
            displayinfo(node.right); 
        } 
    } 
    public void displayphoneno(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
    else { 
       
      System.out.printf("%30s %30s %20s ","Name","Flat Number","Phone number\n"); 
     displayphoneno(this.root); 
    } 
    } 
 
    private void displayphoneno(Node node){ 
      
 
        if (node != null){ 
         displayphoneno(node.left); 
            node.displayno(); 
            displayphoneno(node.right); 
        } 
    } 
    public void displaystatus(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
      System.out.printf("%30s %30s %20s %20s ","Name","Flat 
Number","Flatstatus","Lifestatus\n"); 
     displaystatus(this.root); 
     } 
    } 
 
    private void displaystatus(Node node){ 
      
     if (node != null){ 
         displaystatus(node.left); 
            node.displaystatus(); 
            displaystatus(node.right); 
        } 
    } 
    public void displaymaint(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
       System.out.printf("%20s %20s ","Flat number","Maintainence\n"); 
 
     displaymaint(this.root); 
     } 
    } 
 
    private void displaymaint(Node node){ 
      
        if (node != null){ 
         displaymaint(node.left); 
            node.displaymain(); 
            displaymaint(node.right); 
        } 
    } 
 
 
 
     
    void search(){ 
     if(root==null) { 
      System.out.println("No record present"); 
      return; 
     } 
     int chs; 
     System.out.println("1.Search by Flat number\n2.Search by phone number\nEnter you 
choice"); 
     chs=sc.nextInt(); 
     if(chs==1) { 
        System.out.println("Enter the Flat number to search: "); 
        int fno = sc.nextInt(); 
        Node ptr = root; 
        while(ptr != null){ 
 
            if(fno==ptr.flatno){         
                System.out.println("Found."); 
                System.out.println(" Name: " + ptr.Name); 
                System.out.println(" Flat number: " + ptr.flatno); 
                System.out.println(" Flatstatus: " + ptr.flatstatus); 
                System.out.println(" lifestatus: " + ptr.lifestatus); 
                System.out.println(" phone number: " + ptr.TelephoneNo); 
                return; 
            } 
            else if(fno<ptr.flatno){         
                ptr = ptr.left;                    
            } 
            else{ 
                ptr = ptr.right;                  
            } 
        } 
        System.out.println("Not Found!!!");      
     }  
     if(chs==2) { 
      String phno; 
       do { 
        System.out.println("Enter the phone number to search: "); 
                  phno = sc.next(); 
            if(phno.length()==10) { 
                 break; 
            } 
            else { 
                 System.out.println("Enter valid phone number"); 
                  
            } 
            }while(phno.length()==10); 
              
              
            
            Node ptr = root; 
            while(ptr != null){ 
 
                if(phno.equals(ptr.TelephoneNo)){         
                    System.out.println("Found."); 
                    System.out.println(" Name: " + ptr.Name); 
                    System.out.println(" Flat number: " + ptr.flatno); 
                    System.out.println(" Flatstatus: " + ptr.flatstatus); 
                    System.out.println(" lifestatus: " + ptr.lifestatus); 
                    System.out.println(" phone number: " + ptr.TelephoneNo); 
                    return; 
                } 
                else if(phno.compareTo(ptr.TelephoneNo)<0){         
                    ptr = ptr.left;                    
                } 
                else{ 
                    ptr = ptr.right;                  
                } 
            } 
            System.out.println("Not Found!!!");      
         }  
    } 
 
    void update(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
        System.out.println("Enter the Flat number to update: "); 
        int fno = sc.nextInt(); 
        Node ptr = root; 
        while(ptr != null){ 
            if(fno==ptr.flatno){ 
             System.out.println("1.update Name\n2.update Flat number\n3.update Flatstatus\n"); 
             System.out.println("4.update lifestatus\n5.update telephone number\n 0.Exit"); 
             System.out.println("Enter your choice:"); 
             int ch1; 
             ch1=sc.nextInt(); 
             if(ch1==1) { 
               
              System.out.println("Name"); 
                    System.out.println("Enter first Name: "); 
                    String Namef = sc.next(); 
                    System.out.println("Enter Middle Name: "); 
                    String Namem = sc.next(); 
                    System.out.println("Enter last Name: "); 
                    String Namel = sc.next(); 
                    ptr.Name=Namef+" "+Namem+" "+Namel; 
             } 
             else if(ch1==2) { 
               System.out.println("Enter Flat number: "); 
                     ptr.flatno = sc.nextInt(); 
                     Node ptr1=root; 
                      
              
             while(ptr1!=null) { 
              if(ptr.flatno==ptr1.flatno) { 
               System.out.println("these flat number is already 
present in record"); 
               return; 
              } 
             
               else if(ptr.flatno<ptr1.flatno){         
                           ptr1 = ptr1.left;                    
                       } 
                       else{ 
                           ptr1 = ptr1.right;                  
                       }  
                
               
               
             } 
             
           } 
             else if(ch1==3) { 
               do { 
                        System.out.println("Enter are you owner or tenant: "); 
                           ptr.flatstatus = sc.next(); 
                      if(ptr.flatstatus.equalsIgnoreCase("owner") || ptr.flatstatus.equalsIgnoreCase("tenant")) 
{ 
                           break; 
                      } 
                      else { 
                           System.out.println("Enter correct one"); 
                            
                      } 
                      }while((ptr.flatstatus.equalsIgnoreCase("owner") || 
ptr.flatstatus.equalsIgnoreCase("tenant")!=true)); 
                       
             } 
             else if(ch1==4) { 
               do { 
                      System.out.println("Enter are you family or bachelor: "); 
                         ptr.lifestatus = sc.next(); 
                    if(ptr.lifestatus.equalsIgnoreCase("family") || 
ptr.lifestatus.equalsIgnoreCase("bachelor")) { 
                         break; 
                    } 
                    else { 
                         System.out.println("Enter correct one"); 
                          
                    } 
                    }while((ptr.lifestatus.equalsIgnoreCase("family") || 
ptr.lifestatus.equalsIgnoreCase("bachelor")!=true)); 
                      
                     
             } 
              
             else if(ch1==5) { 
              do { 
                System.out.println("Enter phone number: "); 
                         ptr.TelephoneNo = sc.next();  
               if(ptr.TelephoneNo.length()==10) { 
                               break; 
               } 
               else { 
                System.out.println("Enter valid phone number"); 
               } 
                
             }while(ptr.TelephoneNo.length()!=10); 
             } 
             else if(ch1==0) { 
              break; 
             } 
                 
            } 
 
            else if(fno<ptr.flatno){ 
                ptr = ptr.left; 
            } 
            else{ 
                ptr = ptr.right; 
            } 
        } 
        System.out.println("Not Found");    
     } 
    } 
 
    
    public void delete(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
        System.out.print("Enter the flat number to delete: "); 
        int fno = sc.nextInt(); 
        this.root = delete(this.root, fno); 
        System.out.println("Deleted succesfully"); 
     } 
    } 
 
    private Node delete(Node root, int fno) 
    { 
        
        if (root == null) 
            return root; 
  
        if (fno<root.flatno) 
            root.left = delete(root.left, fno);  
        else if (fno>root.flatno) 
            root.right = delete(root.right, fno); 
  
        else { 
           if (root.left == null) 
                return root.right; 
            else if (root.right == null) 
                return root.left; 
  
            Node temp = getSuccessor(root.right); 
            root.flatno = temp.flatno; 
            root.Name= temp.Name; 
            root.flatstatus=temp.flatstatus; 
            root.lifestatus=temp.lifestatus; 
            root.TelephoneNo=temp.TelephoneNo; 
            root.totalMain=temp.totalMain; 
           
            root.right = delete(root.right, root.flatno); 
        } 
         return root; 
    } 
  
    private Node getSuccessor(Node node) 
    { 
    
      int flatno = node.flatno; 
         String Name= node.Name; 
         String flatstatus=node.flatstatus; 
         String lifestatus=node.lifestatus; 
         String TelephoneNo=node.TelephoneNo; 
         double totalMain=node.totalMain; 
 
        while (node.left != null) 
        { 
          flatno = node.left.flatno;
           Name= node.left.Name; 
             flatstatus=node.left.flatstatus; 
             lifestatus=node.left.lifestatus; 
             TelephoneNo=node.left.TelephoneNo; 
             totalMain=node.left.totalMain; 
 
            node = node.left; 
        } 
        return new Node(Name, flatstatus,lifestatus,flatno,TelephoneNo,totalMain); 
    } 
  
   
    
 
    void sortBt (int choice) 
    { 
      Node ptr, temp; 
      head = tail = root; 
      q.push (tail); 
      ptr = q.peek (); 
 
      do 
        { 
  if (tail.left != null) 
   { temp = tail.left; 
     q.peek ().next = temp; 
     q.push (temp); 
   } 
  if (tail.right != null) 
   { 
     temp = tail.right; 
     q.peek ().next = temp; 
     q.push (temp); 
 
   } 
  if (tail != null) 
   { 
     tail = tail.next; 
   } 
        } 
      while (tail != null); 
 
      if (choice == 3) 
        { 
  ptr = head; 
  root1 = head; 
  while (ptr.next != q.peek ().next) 
   { 
     if (Long.parseLong(ptr.TelephoneNo) <Long.parseLong (ptr.next.TelephoneNo)) 
       { 
     ptr.right1 = ptr.next; 
     ptr = ptr.next; 
       } 
     else if (Long.parseLong(ptr.TelephoneNo)>Long.parseLong(ptr.next.TelephoneNo)) 
       { 
     ptr.left1 = ptr.next; 
     ptr = ptr.next; 
       } 
   } 
 
        } 
 
      else if (choice == 4) 
        { 
  ptr = head; 
  root2 = head; 
  int i = 0; 
  while (ptr.next != q.peek ().next) 
   { 
     if (!ptr.Name.equalsIgnoreCase (ptr.next.Name)&& (int) ptr.Name.charAt (i) ==(int) 
ptr.next.Name.charAt (i)) 
       { 
  i = i++; 
       } 
     else if ((int) ptr.Name.charAt (i) <(int) ptr.next.Name.charAt (i)) 
       { 
  ptr.right2 = ptr.next; 
  ptr = ptr.next; 
       } 
     else if ((int) ptr.Name.charAt (i) >(int) ptr.next.Name.charAt (i)) 
       { 
  ptr.left2 = ptr.next; 
  ptr = ptr.next; 
       } 
   } 
        } 
    } 
 
    void sort_phone (Node ph_node) 
    { 
   if (ph_node == null) 
   { 
  return; 
        } 
      sort_phone (ph_node.left1); 
      System.out.println (ph_node.TelephoneNo + "\t" + ph_node.Name); 
      sort_phone (ph_node.right1); 
    } 
    void sort_Name (Node nm_node) 
    { 
      if (nm_node == null) 
        { 
      return; 
        } 
      sort_Name (nm_node.left2); 
      System.out.println (nm_node.Name + "\t" + nm_node.TelephoneNo); 
      sort_Name (nm_node.right2); 
    } 
    
    void maintenance() { 
     if(root==null) { 
      System.out.println("No record present"); 
      return; 
     } 
     else { 
     int ch6; 
     System.out.println("*********Maintainence*********"); 
     System.out.println("These is for 6 months"); 
     System.out.println("1\tHouse 
keeping\t500\n2\tParking\t\t500\n3\tWatchmen\t500\n4\tGardner\t\t500\n5\tHall 
cleaning\t500"); 
     System.out.println("----------------------------------------------------------------------------------------"); 
     System.out.println("Total Maintainence=2500.0"); 
     System.out.println("1.for paying maintenance\n0.Exit\nEnter your choice"); 
        ch6=sc.nextInt(); 
        if(ch6==1) { 
          
          System.out.println("Enter the Flat number to pay Maintainence: "); 
             int fno = sc.nextInt(); 
             Node ptr = root; 
             while(ptr != null){ 
                 if(fno==ptr.flatno){ 
                  System.out.println("Enter the amount:"); 
                  double amt; 
                  amt=sc.nextInt(); 
                  ptr.totalMain=ptr.totalMain-amt; 
                  if(ptr.totalMain==0) { 
                   System.out.println("Paid.."); 
                   return; 
                      } 
                  else if(ptr.totalMain>0) { 
                   System.out.println("Due Maintainence: "+ptr.totalMain); 
                   return; 
                  } 
                  else { 
               System.out.println("you enter more amount than 2500\nkindly take back "+(
2*ptr.totalMain+ptr.totalMain)+" from admin\nphone Number:123*******"); 
               System.out.println("Paid.."); 
               return; 
                  } 
                 } 
              
                 else if(fno<ptr.flatno){ 
                     ptr = ptr.left; 
                 } 
                 else{ 
                     ptr = ptr.right; 
                 } 
             } 
         
             System.out.println("Not Found");     
         } 
     
 
         
 
         
               else if(ch6==0) { 
         return; 
        } 
        else { 
         System.out.println("Invalid choice"); 
        } 
      
    } 
    } 
    
} 
class Node1{ 
Node1 left, right; 
    String Namew,aow,present,telephoneNo1;//aow=area of work 
    int Id; 
     
        
     
    Node1(int Id,String Namew, String aow,String telephoneNo1,String present){ 
        left = right = null; 
       this.Namew=Namew; 
       this.aow=aow; 
       this.Id=Id; 
       this.telephoneNo1=telephoneNo1; 
       this.present="Not there"; 
        
        
    } 
 
     
    void display(){ 
      
     System.out.printf("%35s %20d %15s %25s %18s 
",this.Namew,this.Id,this.aow,this.telephoneNo1,this.present+"\n"); 
           
          
    } 
} 
 
class BST{ 
 
    Scanner sc = new Scanner(System.in); 
    Node1 root;                              
    BST(){                     
        root = null;                        
    } 
    void create1(){ 
       String Namew,aow,present,telephoneNo1;//aow=area of work 
       int Id; 
 
 
        int  ch; 
        do{ 
         String Namef,Namem,Namel; 
         System.out.println("Name"); 
            System.out.println("Enter first Name: "); 
            Namef = sc.next(); 
            System.out.println("Enter Middle Name: "); 
            Namem = sc.next(); 
            System.out.println("Enter last Name: "); 
            Namel = sc.next(); 
            Namew=Namef+" "+Namem+" "+Namel; 
         System.out.println("Enter Id: "); 
         Id = sc.nextInt(); 
         Node1 ptr1=root; 
          
     
    while(ptr1!=null) { 
     if(Id==ptr1.Id) { 
      System.out.println("these ID is already present in 
record"); 
      return; 
     } 
    
      else if(Id<ptr1.Id){         
                  ptr1 = ptr1.left;                    
              } 
              else{ 
                  ptr1 = ptr1.right;                  
              }  
      } 
    
    do { 
      
     System.out.println("for house keeping enter hk\n-------------------\nfor Parking enter pk\n-------------------\n" 
       + "for watchman enter wm\n------------------
\nfor Gardner enter gr\n-------------------\n" 
       + "for Hall cleaning enter hc\n-------------------  
"); 
     System.out.println("Enter  area of work: "); 
              aow = sc.next();           
if(aow.equalsIgnoreCase("hk") || aow.equalsIgnoreCase("pk")||aow.equalsIgnoreCase("wm") || 
aow.equalsIgnoreCase("gr") || aow.equalsIgnoreCase("hc")) { 
                 break; 
            } 
            else { 
                 System.out.println("Enter correct one\n"); 
                  
            } 
            }while((aow.equalsIgnoreCase("hk") || 
aow.equalsIgnoreCase("pk")||aow.equalsIgnoreCase("wm") || aow.equalsIgnoreCase("gr") || 
aow.equalsIgnoreCase("hc"))!=true); 
              
            
             
            present="Not there"; 
            
          do { 
            System.out.println("Enter phone number: "); 
            telephoneNo1 = sc.next(); 
            
            if(telephoneNo1.length()==10) { 
            Node1 temp1 = new Node1(Id,Namew, aow,telephoneNo1,present);
               if(root == null){       
                root = temp1; 
            } 
            else{ 
                Node1 ptr = root; 
                while(ptr != null){ 
 
                    if(temp1.Id<ptr.Id){ 
                        if (ptr.left == null){ 
                            ptr.left = temp1; 
                            break; 
                        } 
                        else{ 
                            ptr = ptr.left; 
                        } 
                    } 
                    else if(temp1.Id>ptr.Id){ 
                        if (ptr.right == null){ 
                            ptr.right = temp1; 
                            break; 
                        } 
                        else{ 
                            ptr = ptr.right; 
                        } 
                    } 
                    else{ 
                        System.out.println("Already present"); 
                        break; 
                    } 
                } 
            } 
        } 
           else { 
             System.out.println("Enter valid phone number"); 
            } 
            }while(telephoneNo1.length()!=10); 
            System.out.print("\nDo you want to add more Helpers's information ?\nPress '1' to 
continue\nPress '0' to exit :"); 
    ch = sc.nextInt(); 
   System.out.println(""); 
  } while (ch != 0); 
    } 
    public void displayinfo1(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
      System.out.printf("%30s %25s %20s %20s %20s","Name","ID","Area of 
work","Phone number","is there\n"); 
 
     displayinfo1(this.root); 
     } 
    } 
 
    private void displayinfo1(Node1 node1){ 
      
        if (node1 != null){ 
         displayinfo1(node1.left); 
            node1.display(); 
            displayinfo1(node1.right); 
        } 
    } 
    void mark(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
        System.out.println("Enter your Id to mark you are there to work: "); 
        int Id1 = sc.nextInt(); 
        Node1 ptr = root; 
        while(ptr != null){ 
            if(Id1==ptr.Id){ 
                  
               do { 
                System.out.println("Enter present for marking your working day: "); 
                      ptr.present= sc.next(); 
                         if(ptr.present.equalsIgnoreCase("present")) { 
                          System.out.println("Stored successfully"); 
                      break; 
                 } 
                 else { 
                      System.out.println("Enter correct one"); 
                       
                 } 
                 }while(ptr.present.equalsIgnoreCase("present")); 
                   
                            return; 
            } 
            else if(Id1<ptr.Id){ 
                ptr = ptr.left; 
            } 
            else{ 
                ptr = ptr.right; 
            } 
        } 
        System.out.println("Not Found");    
     } 
    } 
 
    public void delete1(){ 
     if(root==null) { 
      System.out.println("No record present"); 
     } 
     else { 
        System.out.print("Enter the Id of helper to delete: "); 
        int Id1 = sc.nextInt(); 
        this.root = delete1(this.root, Id1); 
        System.out.println("Deleted succesfully"); 
     } 
    } 
 
    private Node1 delete1(Node1 root, int Id1) 
    { 
        
        if (root == null) 
            return root; 
  
        if (Id1<root.Id) 
            root.left = delete1(root.left, Id1); 
        else if (Id1>root.Id) 
            root.right = delete1(root.right, Id1); 
  
        else { 
           if (root.left == null) 
                return root.right; 
            else if (root.right == null) 
                return root.left; 
  
            Node1 temp = getSuccessor(root.right); 
            root.Id = temp.Id; 
            root.Namew= temp.Namew; 
            root.aow=temp.aow; 
            root.telephoneNo1=temp.telephoneNo1; 
            root.present=temp.present; 
           
            root.right = delete1(root.right, root.Id); 
        } 
         return root; 
    } 
  
    private Node1 getSuccessor(Node1 node1) 
    { 
    
      int Id = node1.Id; 
         String Namew= node1.Namew; 
         String aow=node1.aow; 
         String telephoneNo1=node1.telephoneNo1; 
         String present=node1.present; 
       
 
        while (node1.left != null) 
        { 
           Id = node1.left.Id; 
              Namew= node1.left.Namew; 
              aow=node1.left.aow; 
              telephoneNo1=node1.left.telephoneNo1; 
              present=node1.left.present; 
           
                     node1 = node1.left; 
        } 
        return new Node1(Id,Namew, aow,telephoneNo1,present); 
    } 
  
   
 
 
} 
class Hall1{ 
 int hall_number; 
    int price;  
    String date; 
    String Name,phonenumber; 
 Hall1 next,prev; 
  
 Hall1(int price1,String datee,String name,String phoneno,int hall__number){ 
  hall_number=hall__number; 
  price=price1; 
  date=datee; 
  Name=name; 
  phonenumber=phoneno; 
  prev=next=null; 
   
 } 
} 
class BookHall1{ 
 Hall1 head,temp,rear; 
 Scanner sc=new Scanner(System.in); 
 boolean isempty() { 
  if(head==null) 
   return true; 
  else 
   return false; 
 } 
  
 void Book1() {  
  Hall1 h1=new Hall1(0,null,null,null,0); 
   System.out.println("There are 2 halls in society\nhall\tcapacity\trent for one 
day\n1\t100\t\t\t5000\n2\t400\t\t\t10000");   
   System.out.println("only if you want to book hall within next 15 days"); 
   System.out.println("Enter the Hall number which you want to book:"); 
   int Hallnumber=sc.nextInt(); 
    switch(Hallnumber) { 
   case 1: 
   
    System.out.println("Enter your name for booking the hall"); 
                System.out.println("Enter first Name: "); 
                String Namef1 = sc.next(); 
                System.out.println("Enter Middle Name: "); 
                String Namem1 = sc.next(); 
                System.out.println("Enter last Name: "); 
                String Namel1 = sc.next(); 
                String name1=Namef1+" "+Namem1+" "+Namel1; 
    
     
    String phoneno1; 
    do { 
           System.out.println("Enter phone your number: "); 
                    phoneno1= sc.next(); 
                    sc.nextLine(); 
          if(phoneno1.length()==10) { 
           
          } 
          else { 
           System.out.println("Enter valid phone number"); 
          } 
           
        }while(phoneno1.length()!=10); 
        
     System.out.println("Enter the date in the format 
day/month/year(00/00/0000):"); 
     String date1=sc.next(); 
     temp=head; 
     
     if(temp==null) { 
      h1=new Hall1(5000,date1,name1,phoneno1,1); 
      System.out.println("HAll BOOKED :)"); 
 
      break; 
       } 
     else { 
     while(temp!=null) { 
      if(date1.equals(temp.date)) { 
       System.out.println("these date is booked 
already\nchosse another one"); 
       temp=temp.next; 
       return; 
      } 
      else {  
       h1=new Hall1(5000,date1,name1,phoneno1,1); 
       System.out.println("HAll BOOKED :)"); 
 
       break; 
        
      } 
     } 
     break; 
 
         } 
         case 2: 
     
    System.out.println("Enter your name for booking the hall"); 
                System.out.println("Enter first Name: "); 
                String Namef2 = sc.next(); 
                System.out.println("Enter Middle Name: "); 
                String Namem2 = sc.next(); 
                System.out.println("Enter last Name: "); 
                String Namel2 = sc.next(); 
                String name2=Namef2+" "+Namem2+" "+Namel2; 
 
    String phoneno2; 
    do { 
           System.out.println("Enter phone your number: "); 
                    phoneno2= sc.next();  
          if(phoneno2.length()==10) { 
          
          } 
          else { 
           System.out.println("Enter valid phone number"); 
          } 
           
        }while(phoneno2.length()!=10); 
        
     System.out.println("Enter the date in the format 
day/month/year(00/00/0000):"); 
     String date2=sc.next(); 
     temp=head; 
      
     if(temp==null) { 
      h1=new Hall1(10000,date2,name2,phoneno2,2); 
      System.out.println("HAll BOOKED"); 
      break; 
       } 
     else { 
     while(temp!=null) { 
      if(date2.equals(temp.date)) { 
       System.out.println("these date is booked 
already\nchosse another one"); 
        
       temp=temp.next; 
       return; 
      } 
      else {  
       h1=new Hall1(10000,date2,name2,phoneno2,2); 
       System.out.println("HAll BOOKED"); 
 
       break; 
        
      } 
     } 
     break; 
 
         } 
 
           default:  
    System.out.println("Wrong input of choice"); 
   } 
   if(h1.hall_number!=0) { 
    if(isempty()) 
     head=h1; 
    else { 
     temp=head; 
     while(temp.next!=null) 
      temp=temp.next; 
     h1.prev=temp; 
     temp.next=h1; 
    } 
   } 
    
    
   
 } 
 void delete(){  
  if(isempty()) 
   System.out.println("No booking are there :)"); 
  else { 
   System.out.println("bookings are: "); 
   System.out.println("Name: "+head.Name+"\nnumber: 
"+head.phonenumber+"Hall number: "+head.hall_number+"\nprice: "+head.price+"\nDate: 
"+head.date); 
   if(head.next==null) 
    rear=head; 
   head=head.next; 
   System.out.println("Deleted succesfully"); 
  } 
 } 
 void display(){  
  if(isempty()) 
   System.out.println("No bookings are there"); 
  else { 
   System.out.println("bookings are: "); 
   temp=head; 
    System.out.printf("%30s %30s %30s %15s %20s ","Name","phone 
number","booked hall number","rent","date\n"); 
   while(temp!=null) { 
    System.out.printf("%35s %22s %23s %25s %20s 
",temp.Name,temp.phonenumber,temp.hall_number,temp.price,temp.date+"\n"); 
    System.out.println(); 
    temp=temp.next; 
   } 
  } 
 } 
 
 } 
 
 
public class SocietyWork { 
  public static void main(String[] args) { 
         BinarySearchTree tree = new BinarySearchTree(); 
         BST b=new BST(); 
         BookHall1 bh1=new BookHall1(); 
         Scanner sc = new Scanner(System.in); 
         int ch; 
         System.out.println("******************Welcome to dreams 
Society******************"); 
         System.out.println("Total number of flats:30"); 
         int ch1; 
         do { 
         System.out.println("--------------------------------------"); 
         System.out.println("1)Admin\n2)Society Member\n3)other than society related 
person\n4)Helpers\n0)Exit"); 
         System.out.println("--------------------------------------"); 
         System.out.println("Enter who you are:"); 
         ch1=sc.nextInt(); 
          
         if(ch1==1) { 
          String password; 
          System.out.println("Enter password:"); 
          password=sc.next(); 
          if(password.equals("ssva")) { 
             do{ 
         
 System.out.println("**********************************************\n\t\tMENU\n*
 ********************************************\n1.Add a Society Member's record\n" + 
                                            "2.phone directory of Society Member\n"  
+  
                                            "3.Update Society Member information\n" 
+ 
                                            "4.display Society Member about Status\n" 
+ 
                                            "5.display Society Member Information\n" 
+ 
                                            "6.search Society Member Information\n" 
+ 
                                            "7.delete Society Member Information\n" 
+ 
                                            "8.maintenance\n"+ 
                                            "9.Booking\n"+ 
                                            "10.display Maintainence Information\n"+ 
                                            "11.Add a Helpers record\n"+ 
                                            "12.delete Helpers Information\n"+ 
                                            "13.display Helpers Information\n"+ 
                                             
"0.Exit.\n*********************************************"); 
                         System.out.println("Enter the choice: "); 
                         ch = sc.nextInt(); 
                        sc.nextLine(); 
 
               if (ch == 0) 
                       break; 
 
             switch(ch){ 
                  case 1 : 
                   
                          tree.create(); 
                          break; 
                    
                 case 2:  
                 System.out.println("1.display\n2.Search\n3.Sort by phone 
no.\n4.Sort by name\n0.Exit"); 
                       System.out.println("Enter your choice"); 
                                    int n; 
                                    n=sc.nextInt(); 
                                    
                                 do { 
                                   if(n==1) { 
                                    System.out.println("----------------------------------------------------------------------------------------------------------------"); 
                                     tree.displayphoneno(); 
                                      System.out.println("-------------------------------------------------------------------------------------------------------------\n"); 
                                     break; 
                                    } 
                                     
                                    else if(n==2) { 
                                     tree.search(); 
                                     break; 
                                    } 
                                    else if (n == 3) 
                                    { 
                                      tree.sortBt (3); 
                                      tree.sort_phone (tree.root1); 
                                      break; 
                                    } 
                                   else if (n == 4) 
                                    { 
                                      tree.sortBt (4); 
                                      tree.sort_Name (tree.root2); 
                                      break; 
                                    } 
                                 }while(n!=0); 
                                    break; 
                             case 3: 
                              tree.update(); 
                              break; 
                             case 4: 
                               System.out.println("----------------------------------------------------------------------------------------------------------------------------"); 
                                 tree.displaystatus();  
                                 System.out.println("---------------------------------------------------------------------------------------------------------------------------\n"); 
                                 break; 
                             case 5: 
                               System.out.println("----------------------------------------------------------------------------------------------------------------------------------------------------------"); 
                                 tree.displayinfo(); 
                                 System.out.println("---------------------------------------------------------------------------------------------------------------------------------------------------------\n"); 
                                 break; 
                             case 6: 
                              tree.search(); 
                              break; 
                             case 7: 
                              tree.delete(); 
                              break; 
                             case 8: 
                                 tree.maintenance();       
                                 break; 
                             case 9: 
                              int ch8; 
      System.out.println("1.for booking the hall\n2.for display the booked date record\n3.for 
delete the booked date\n0.Exit"); 
                           ch8=sc.nextInt(); 
                           if(ch8==1) { 
                            bh1.Book1(); 
                           } 
                           else if(ch8==2) { 
                             System.out.println("-------------------------------------------------------------------------------------------------------------------------"); 
                            bh1.display(); 
                             System.out.println("------------------------------------------------------------------------------------------------------------------------\n"); 
                           } 
                           else if(ch8==3) { 
                            bh1.delete(); 
                           } 
 
                           else if(ch8==0) { 
                            System.out.println("if you want to 
know another information contact admin\nphone number:123*******"); 
                             
                           } 
                           else { 
                            System.out.println("Invalid 
choice.."); 
                           } 
                           
                              break; 
                             case 10: 
                               System.out.println("--------------------------------------------------------------------------------------"); 
                              tree.displaymaint(); 
                               System.out.println("--------------------------------------------------------------------------------------\n"); 
                              break; 
                             case 11: 
                              b.create1(); 
                              break; 
                             case 12: 
                              b.delete1(); 
                              break; 
                             case 13: 
                               System.out.println("--------------------------------------------------------------------------------------------------------------"); 
                              b.displayinfo1(); 
                               System.out.println("---------------------------------------------------------------------------------------------------------------\n"); 
                              break; 
                             default: 
                                 System.out.println("Invalid Option"); 
                                 break; 
                         } 
                     } while(ch!= 0); 
          } 
          else { 
           System.out.println("Wrong password!!"); 
           System.out.println("-------------------"); 
           } 
           
         } 
         else if(ch1==2) { 
           
          String password; 
          System.out.println("Enter password:"); 
          password=sc.next(); 
          if(password.equals("dream@123")) { 
           do{ 
              
 System.out.println("\t\tMENU\n*********************************************\n1.
 display phone number\n" + 
                                                          "2.display about Status\n"+ 
                                                 "3.display Information\n" + 
                                                 "4.search Information\n" + 
                                                 "5.Booking\n"+ 
                                                 "6.Maintainence\n"+ 
                                                 "7.display Maintainence 
Information\n"+ 
                                                 "8.display helpers Information\n"+ 
                                                 
"0.Exit.\n*********************************************"); 
                              System.out.println("Enter the choice: "); 
                              ch = sc.nextInt(); 
                             sc.nextLine(); 
 
                    if (ch == 0) 
                            break; 
 
                  switch(ch){ 
                                   
                                   case 1:  
                                    System.out.println("-------------------------------------------------------------------------------------------------------------------------------------------"); 
                                      tree.displayphoneno(); 
                                      System.out.println("------------------------------------------------------------------------------------------------------------------------------------------\n"); 
                                         break; 
                                  case 2: 
                                   System.out.println("-------------------------------------------------------------------------------------------------------------------------------------------"); 
                                      tree.displaystatus();   
                                      System.out.println("------------------------------------------------------------------------------------------------------------------------------------------\n"); 
                                      break; 
                                   case 3: 
                                    System.out.println("-------------------------------------------------------------------------------------------------------------------------------------------"); 
                                      tree.displayinfo();  
                                      System.out.println("------------------------------------------------------------------------------------------------------------------------------------------\n"); 
                                      break; 
                                   case 4: 
                                   tree.search(); 
                                   break; 
                                   case 5: 
                                             int ch2; 
                      System.out.println("1.for booking the hall\n2.for display the booked date 
record\n0.Exit"); 
                                      ch2=sc.nextInt(); 
                                          if(ch2==1) { 
                                                bh1.Book1(); 
                                } 
                                else if(ch2==2) { 
                                  System.out.println("------------------------------------------------------------------------------------------------------------------------------------"); 
                                 bh1.display(); 
                                  System.out.println("-----------------------------------------------------------------------------------------------------------------------------------\n"); 
                                } 
                                else if(ch2==0) { 
                                 System.out.println("if you 
want to know another information contact admin\nphone number:123*******"); 
                                  
                                } 
                                else { 
                                 System.out.println("Invalid 
choice.."); 
                                } 
                                 
                                   break; 
                                   case 6: 
                                    tree.maintenance(); 
                                    break; 
                                   case 7: 
                                    System.out.println("--------------------------------------------------------------------------------------------------------------------------------------------"); 
                                    tree.displaymaint(); 
                                    System.out.println("--------------------------------------------------------------------------------------------------------------------------------------------
\n"); 
                                    break; 
                                   case 8: 
                                    System.out.println("--------------------------------------------------------------------------------------------------------------------------------------------
"); 
                                    b.displayinfo1(); 
                                    System.out.println("---------------------------------------------------------------------------------------------------------------------------------------------
\n"); 
                                    break; 
                                  
                                  default: 
                                      System.out.println("Invalid Option"); 
                                      break; 
                              } 
                         } while(ch!= 0); 
          } 
                
               else { 
                System.out.println("Wrong password!!"); 
                } 
         
 
           
   
             
           
         } 
          
         else if(ch1==3) { 
          int ch2; 
          System.out.println("1.for booking the hall\n2.for display the booked date 
record\n0.Exit"); 
          ch2=sc.nextInt(); 
          if(ch2==1) { 
           bh1.Book1(); 
          } 
          else if(ch2==2) { 
            System.out.println("------------------------------------------------------------------------------------------------------------------------------------"); 
           bh1.display(); 
            System.out.println("------------------------------------------------------------------------------------------------------------------------------------\n"); 
          } 
          else if(ch2==0) { 
           System.out.println("if you want to know another information contact 
admin\nphone number:123*******"); 
            
          } 
          else { 
           System.out.println("Invalid choice.."); 
          } 
           
         } 
         else if(ch1==4) { 
          String password1; 
          System.out.println("Enter password:"); 
          password1=sc.next(); 
          if(password1.equals("vssa")) { 
          int ch10; 
          System.out.println("do you want to mark yourself present??\npress 1\nif not press 
0"); 
          ch10=sc.nextInt(); 
          if(ch10==1) { 
           b.mark(); 
          } 
          else if(ch10==0) { 
           System.out.println("if you want to know another information contact 
admin\nphone number:123*******"); 
            
          } 
          else { 
           System.out.println("Invalid choice.."); 
          } 
           
         } 
          else { 
           System.out.println("Wrong password!!"); 
           System.out.println("-------------------"); 
           } 
         } 
   
         else if(ch1==0) { 
          System.out.println("Here the journey of dreams society ends........."); 
          break; 
         } 
         else  
             { 
          System.out.println("invalid choice"); 
               } 
 
        
         
         }while(ch1!=0);     
         sc.close(); 
} 
} 
/* 
* ******************Welcome to dreams Society****************** 
Total number of flats:30 -------------------------------------- 
1)Admin 
2)Society Member 
3)other than society related person 
4)Helpers 
0)Exit -------------------------------------- 
Enter who you are: 
1 
Enter password: 
ssva 
********************************************** 
MENU 
********************************************* 
1.Add a Society Member's record 
2.phone directory of Society Member 
3.Update Society Member information 
4.display Society Member about Status 
5.display Society Member Information 
6.search Society Member Information 
7.delete Society Member Information 
8.maintenance 
9.Booking 
10.display Maintainence Information 
11.Add a Helpers record 
12.delete Helpers Information 
13.display Helpers Information 
0.Exit. 
********************************************* 
Enter the choice:  
1 
Enter Flat number:  
7 
Name 
Enter first Name:  
sakshi 
Enter Middle Name:  
manoj 
Enter last Name:  
deshmukh 
Enter are you owner or tenant:  
owner 
Enter are you family or bachelor:  
family 
Enter phone number:  
7418520963 
*******Record stored succesfully*******
