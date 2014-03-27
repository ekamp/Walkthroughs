#UITableView General Setup

##Storyboard Setup
1. First add a UITableView to your storyboard by dragging from the panel and either add it to a current view controller or create a new view controller
2. Next Select your TableView and within the attributes inspector(fourth option) make sure dynamic cells are enabled and set prototype cells to 1
3. Now select the prototype cell set its style to Subtitle and its id to mytableviewcell (Or whatever you want to refer to it as)
4. Lastly create an IBOutlet for the Tableview by holding control and clicking on the Tableview, then clicking within the @interface section of your view controller(.m file)

##Table Data Creation
1. First create your blank array within the @interface section


    @property (strong, nonatomic) NSMutableArray *tableArray;

2. Next we must tell the table what source of data it will be using to populate the table, so we must set the table view data source, and we must allocate for the array in which we will be storing our table data.


    self.tableView.dataSource = self;
    self.tableArray = [[
