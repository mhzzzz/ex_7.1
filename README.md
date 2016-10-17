# ex_7.1
统计卖出书本的ID，数量，总价钱的初级程序版本
问题在于：
比如连续三次输入同一本书A，第四次输入第二本不同的书B，第五次，第六次再输入第一本书A，则第一本书的统计信息在第四次已经被书B覆盖，书A的数量又只是第五次、第六次的和。

    //这个程序的工作是将每种ID不同的书的ID,卖出总数，总价钱输出
    //还不是任意输入不同的信息，前后不同顺序输入的信息还可以叠加。 

    #include<iostream>
    #include<string>

    using std::cout;
    using std::endl;
    using std::cin;
    using std::string; 

    struct Sales_data{
	    std::string bookNo;
	    unsigned units_sold = 0;
	    double revenue = 0.0;
    }; 

    int main()
    {
	    Sales_data total;
	    if(cin>>total.bookNo>>total.units_sold>>total.revenue){
	    	Sales_data trans;
		    while(cin>>trans.bookNo>>trans.units_sold>>trans.revenue){
			    if(total.bookNo == trans.bookNo){
			    	total.revenue += trans.revenue;
			    	total.units_sold += trans.units_sold;
		    	}
	    		else{
		    		cout<<"Book ID: "<< total.bookNo <<endl;
		    		cout<<"Book Revenue: "<< total.revenue <<endl;
		    		cout<<"Book sold: "<< total.units_sold <<endl;
		    		cout<<endl;
		    		total = trans;
		    	}
	    	}
		
	    	cout<<"Book ID: "<< total.bookNo <<endl;
	    	cout<<"Book Revenue: "<< total.revenue <<endl;			
	    	cout<<"Book sold: "<< total.units_sold <<endl;
	    	cout<<endl;
    	}
    	else{
	    	cout<<"No Data? "<<endl;
    	}
	
	    return 0;
    }
