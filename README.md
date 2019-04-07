# sheet2


public class LinkedList{
    private LinkedListNode head=null;
    private double sum=0.0;
    private double average;
    private double median;
    private int maximum;
    private int minimum;
    public void print(){
        LinkedListNode i=head;
        while(i!=null){
            System.out.println(i.value);
            i=i.next;
        }
    }
    public void add(int v,int index){
        LinkedListNode n = new LinkedListNode();
        n.value=v;
        if(index==0){
            n.next=head;
            head=n;
            sum+=head;
        }else if(index>0){
            LinkedListNode k=head;
            int a,b=0;
            for(a=0;a<index-1;a++){
                k=k.next;
                sum+=k.value;
                b++;
            }
            n.next=k.next;
            k.next=n;
            LinkedListNode m=head;
            for(a=0;a<(index-1)/2;a++){
                m=m.next;
            }
            int s=-1;
            LinkedListNode x=head;
            for(a=0;a<index-1;a++){
                x=x.next;
                if(s<x.value){
                    maximum=x.value;
                    s=maximum;
                }
            }
            int f=1000000;
            LinkedListNode g=head;
            for(a=0;a<index-1;a++){
                g=g.next;
                if(f>g.value){
                    minimum=g.value;
                    f=minimum;
                }
            }
            median=m.value;
            average=sum/b;
        }else{
            System.out.println("ERROR");
            return;
        }
    }
    public void remove(int index){
        if(index==0){
            head=head.next;
        }
        else if(index>0){
            LinkedListNode i=head;
            int a;
            for(a=0;a<index-1;a++){
                i=i.next;
            }
            LinkedListNode j=i.next;
            i.next=j.next;
        }else{
            System.out.println("ERROR");
            return;
        }
    }
    public double[] summary(LinkedListNode head) {
        double[] res;
        res[0] = sum;
        res[1] = average;
        res[2] = median;
        res[3] = (double)maximum;
        res[4] = (double)minimum;
        return res;
    }
    public LinkedListNode reverse(LinkedListNode head){
        LinkedListNode prev=null;
        LinkedListNode next=null;
        while(head!=null){
            next=head.next;
            head.next=prev;
            prev=head;
            head=next;
        }
        return prev;
    }
    public static LinkedListNode evenIndexedElements(LinkedListNode head){
        LinkedListNode i=head;
        LinkedListNode h=head;
        while(i!=null){
            i=i.next;
            i=i.next;
            h=i;
        }
        return h;
    }
    public static LinkedListNode insertionSort(LinkedListNode head){
        if(head==null||head.next==null){
            return head;
        }
        LinkedListNode n;
        n=head.value;
        LinkedListNode p;
        p=head.next;
        while(p!=null){
            LinkedListNode i=n;
            LinkedListNode e=p.next;
            if(p.value<=n.value){
                LinkedListNode o=n;
                n=p;
                n.next=o;
            }else{
                while(i.next!=null){
                    if(p.value>i.value&&p.value<=i.next.value){
                        LinkedListNode o=i.next;
                        i.next=p;
                        p.next=o;
                    }
                    i=i.next;
                }
                if (i.next == null && p.value>i.value){
                    i.next=p;
                    p.next=null;
                }
            }
            p=e;
        }
        return n;
    }
    public static LinkedListNode mergeSort(LinkedListNode head){
        if(head==null||head.next==null){
            return head;
        }
        LinkedListNode a=head;
        LinkedListNode b=head.next;
        while(b!=null&&b.next!=null){
            head=head.next;
            head.next=null;
            LinkedListNode temp=new LinkedListNode();
            LinkedListNode h=temp;
            LinkedListNode c=h;
            while(a!=null&&b!=null){
                if(a.value<b.value){
                    c.next=a;
                    c=a;
                    a=a.next;
                }else{
                    c.next=b;
                    c=b;
                    b=b.next;
                }
            }
            if(a==null){
                c.next=b;
            }else{
                c.next=a;
            }
            return h.next;
        }
    }
    public static LinkedListNode removeCentralNode(LinkedListNode head){
        if(head==null||head.next==null){
            return head;
        }
        LinkedListNode a =head;
        int c=0,b;
        while(a!=null){
            a=a.next;
            c++;
        }
        for(b=0;b<c/2;c++){
            a=a.next;
        }
        LinkedListNode j=a.next;
        a.next=j.next;
    }
    public static boolean palindrome(LinkedListNode head){
        if(head==null){
            return true;
        }
        LinkedListNode p=head;
        LinkedListNode prev=head.value;
        while (p.next!=null){
            LinkedListNode temp=p.next.value;
            temp.next=prev;
            prev=temp;
            p=p.next;
        }
        LinkedListNode p1=head;
        LinkedListNode p2=prev;
        while(p1!=null){
            if(p1.value!=p2.value){
                return false;
            }
            p1=p1.next;
            p2=p2.next;
        }
        return true;
    }
}
