#UITableView General Setup

##Storyboard Setup
1. First add a UITableView to your storyboard by dragging from the panel and either add it to a current view controller or create a new view controller
2. Next Select your TableView and within the attributes inspector(fourth option) make sure dynamic cells are enabled and set prototype cells to 1
3. Now select the prototype cell set its style to Subtitle and its id to myTableViewCell (Or whatever you want to refer to it as)
4. Lastly create an IBOutlet for the Tableview by holding control and clicking on the Tableview, then clicking within the @interface section of your view controller(.m file)

##Table Data Creation and implementation
1. First create your blank array within the @interface section


    @property (strong, nonatomic) NSMutableArray *tableArray;

2. Next we must tell the table what source of data it will be using to populate the table, so we must set the table view data source, and we must allocate for the array in which we will be storing our table data.


    self.tableView.dataSource = self;
    self.tableArray = [[NSMytableArray alloc]init];
    
3. In addition to changing things within our viewcontroller we must look at the viewcontroller header file in order to tell ios that we have a UITableview.</br>Therefore add the following to tell the compiler/program that we are using a tableview


        @interface MyViewController : UIViewController <UITableViewDataSource,UITableViewDelegate>

4. After completing those steps we now must tell iOS how many row we have in our table in order to correctly allocate memory.


        -(NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section 
        {
            return [self.tableArray count];
        }

5. Finally we have to implement the cellForRowAtIndex function in order tell our TableView what we want our cells to contain.


    -(UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath 
    {
        static NSString *cellIdentifier = @"myTableViewCell";
        UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:cellIdentifier];
        NSString *tableInformation = [self.tweetsArray objectAtIndex:indexPath.row];
        [cell.textLabel setText:tableInformation];
        [cell.detailTextLabel setText:@"Some additional information we wish to display"];
        return cell;
    }

Then run your program to check that your information is there!!
    
