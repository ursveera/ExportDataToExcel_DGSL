# ExportDataToExcel_DGSL


	using ExportDataToExcel_DGSL;
	
	
        static void Main(string[] args)
        {
            try
            {
            
            DataTable dt=new DataTable();          
            ExportDataToExcel_SSG.ExportDataTableToExcel(dt, "d:\Filename.xls");//single datatable to excel
            DataTable[] dd = new DataTable[10];
            ExportDataToExcel_SSG.MergingMultiDataTableAs_singleExcelSheet(dd, "d:\File.xls,false);
            ExportDataToExcel_SSG.MultiDataTableAs_MultiExcelFile(dd, "d:\File.xls");           
            DataSet ds=new DataSet();
            ExportDataToExcel_SSG.MergingMultiDataSetAs_singleExcelSheet(ds, "d:\File.xls",false);
           
            }
            catch (Exception)
            {

                throw;
            }
	    
            
        }
/////////////////////////////



		------documenttation

		ExportDataToExcel_SSG.ExportDataTableToExcel

		1.	ExportDataTableToExcel

		ExportDataTableToExcel(DataTable dt, string path)

		Param1: Datatable value
		Param2: Path of the file where you want to save the excel eg.C:/Filename.xls

		2.	MergingMultiDataTableAs_singleExcelSheet

		MergingMultiDataTableAs_singleExcelSheet(DataTable[] dt, string path, bool n_Columns)

		DataTable[] Dt=new DataTable[3];
		Dt[0]=new DataTable();
		Dt[0]=new DataTable();
		Dt[0]=new DataTable();
		Param1: Collection Of Datatable
		Param2: Path of the file where you want to save
		Param3: true or false
				If false
				First datatable columns for values
				If True
				Merging All datatable values as single sheet with each columns     
		Result Like:
		If True:
		One	two	Three  ---- DataTable1
		  1	2	3
		4	5	6
		7	8	9
		Four	Five	Six   ---- DataTable 2
		1	2	3
		4	5	6
		7	8	9

		If False
		One	two	Three  ----DataTable1 Columns
		  1	2	3
		4	5	6
		7	8	9
		1	2	3      ----- DataTable2 Values Started From
		4	5	6
		7	8	9
		

		3.	MultiDataTableAs_MultiExcelFile

		MultiDataTableAs_MultiExcelFile(DataTable[] dt, string path)

		Param1: Array of dataTable
		Param2: Where you want to save the excel file

		In this Each datatable saving as separate Excel file
		Like Total DataTable is 3;
		So saving 	Dt0 as Filename.xls
				Dt1 as Filename_0.xls
				Dt2 as Filename_1.xls
		With whatever the column headers.

		4.	MergingMultiDataSetAs_singleExcelSheet

		Same as 2nd Point.
		Instead of datatable it is dataset
		Dataset ds=new DataSet();
		Ds.tables.add(dt1);
		Ds.tables.add(dt2);
		Ds.tables.add(dt3);

		MergingMultiDataSetAs_singleExcelSheet(DataSet ds, string path, bool n_Columns)

		Param1: Dataset Collection of tables
		Param2: Path of the file where do you want to save the excel
		Param3: true or false

		Conclusion:

		ExportDataToExcel_SSG is a library for export datatable to excel very easily without any dependency. Easily export 			multiple datatable as multi excel file. Dataset as excel sheet. Merging many datatables as single sheet.
		Merging dataset as single sheet. Easy Exception Identification

		Nugget Link:  https://www.nuget.org/packages/ExportDataToExcel_SSG.ExportDataTableToExcel/
		Supported Frame work: 4.5
		Architecture : 32 and 64 system
		Package Manager Console:  Install-Package ExportDataToExcel_SSG.ExportDataTableToExcel -Version 1.0.0
		Dependency : NULL

		In Future Update:

		It will export multi datatable as single excel file with multiple sheets.
		
		####################################################################################		

    class Program
    {
        
        static void Main(string[] args)
        {

            Program p = new Program();
            p.dttoExcelSingle(@"d:\DemoSingleDaTatableToExcel.xls");
            p.MergeManyDatatabletoSingleExcel(@"d:\ManyDatatableasSingleExcel.xls");
            p.ArrayOfDtToMultiExcel(@"d:\Filename.xls");

        }
        public void dttoExcelSingle(string path)
        {
            DataTable dt = new DataTable();
            dt.Clear();
            dt.Columns.Add("Name");
            dt.Columns.Add("Marks");
            DataRow veera = dt.NewRow();
            veera["Name"] = "Demo";
            veera["Marks"] = "500";
            dt.Rows.Add(veera);

            ExportDataToExcel_SSG.ExportDataTableToExcel(dt, path);
        }
        public void MergeManyDatatabletoSingleExcel(string path)
        {
            DataTable[] dd = new DataTable[3];
            dd[0] = new DataTable();
            dd[1] = new DataTable();
            dd[0].Clear();
            dd[0].Columns.Add("Sno");
            dd[0].Columns.Add("Name");
            dd[0].Columns.Add("Phone");
            dd[0].Columns.Add("address");
            DataRow dr1 = dd[0].NewRow();
            dr1["Sno"] = 1;
            dr1["Name"] = "Sample";
            dr1["Phone"] = "1245645690";
            dr1["address"] = "Pondicherry";
            dd[0].Rows.Add(dr1);

            dd[1].Clear();
            dd[1].Columns.Add("Sno");
            dd[1].Columns.Add("Name");
            dd[1].Columns.Add("Phone");
            dd[1].Columns.Add("address");
            DataRow dr2 = dd[1].NewRow();
            dr2["Sno"] = 100;
            dr2["Name"] = "Sample";
            dr2["Phone"] = "9876543210";
            dr2["address"] = "Pondicherry";
            dd[1].Rows.Add(dr2);
            ExportDataToExcel_SSG.MergingMultiDataTableAs_singleExcelSheet(dd, path, false);  //true means with column header of datatables , false means merge all datatables rows with first datatable column header

            
        }
        public void ArrayOfDtToMultiExcel(string path)
        {
            DataTable[] dd = new DataTable[3];
            dd[0] = new DataTable();
            dd[1] = new DataTable();
            dd[0].Clear();
            dd[0].Columns.Add("Sno");
            dd[0].Columns.Add("Name");
            dd[0].Columns.Add("Phone");
            dd[0].Columns.Add("address");
            DataRow dr1 = dd[0].NewRow();
            dr1["Sno"] = 1;
            dr1["Name"] = "Sample";
            dr1["Phone"] = "1245645690";
            dr1["address"] = "Pondicherry";
            dd[0].Rows.Add(dr1);

            dd[1].Clear();
            dd[1].Columns.Add("Sno");
            dd[1].Columns.Add("Name");
            dd[1].Columns.Add("Phone");
            dd[1].Columns.Add("address");
            DataRow dr2 = dd[1].NewRow();
            dr2["Sno"] = 100;
            dr2["Name"] = "Sample";
            dr2["Phone"] = "9876543210";
            dr2["address"] = "Pondicherry";
            dd[1].Rows.Add(dr2);
            ExportDataToExcel_SSG.MultiDataTableAs_MultiExcelFile(dd, path);

        }
    }

