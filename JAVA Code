public class WorkOrderClass {
    public static void workOrder(List<WorkOrder_ID__C> newListWorkOrder){
        Map<Integer, List<String>> maptotech = new map<Integer,List<String>>();
        integer num = 0;
        List<WorkOrder_ID__c> properWo = new List<WorkOrder_ID__c>();
        List<Assignment__c> lstAssignment = new List<Assignment__c>();
        List<Techniciancsv__c> techniciantoAssignment = new List<Techniciancsv__c>();
        for(WorkOrder_ID__c iter : newListWorkOrder){
            List<String> lststring = new List<string>(); 
            If(iter.Service_Type__c != null && iter.Location__c != null ){
                num = num+1;
                properWo.add(iter);
                lststring.add(iter.Service_Type__c);
                lststring.add(iter.Location__c);

                maptotech.put(num,lststring);
            } 
        }
        Map<integer,Id> techId = new Map<integer,Id>();
        Map<Id,Techniciancsv__c> allTechnician = new Map<Id,Techniciancsv__c>([SELECT Id, Name, Phone__c, Location__c, Skills__c, Availibility__c, Name__c, Email__c FROM Techniciancsv__c]);
        integer num2 = 0;
        For(Techniciancsv__c T : allTechnician.values()){
            num2 = num2+1;
            if(maptotech.get(num2) != null){
                List<string> valofmap = maptotech.get(num2);
            system.debug('error 1 ----> the maptotech is empty ---> ' + maptotech.get(num2));
            if(valofMap.contains(t.Skills__c) && ValofMap.contains(t.Location__c) && t.Availibility__c == 'Available'){
                techid.put(num2,t.Id);
            }
            }
           
        }
        integer num3 = 0;
        For(WorkOrder_ID__c W : properWo){
            num3 = num3 + 1;
            Assignment__c A = new Assignment__c();
            A.WorkOrder_ID__c = W.Id;
            A.Technician_csv__c = techid.get(num3);
            lstAssignment.add(A);
        }
        If(!lstAssignment.IsEmpty()){
            insert lstAssignment;
        }
    }
}
