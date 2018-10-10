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
            //Export array of datatatable  to Excel sheet
            //dd array of datatatable
            //"filename"
            //true or false --false means Merging Datatables With its Columns
            //Like col1 col2 col3 ---datatable 1 column headers
            //        1     2   3
            //        4     5   6
            //       Col1  col2 col3 ---datatable 2 column headers
            //        1     2     3
            //        1     44    33
            //true means datatable 1 columns for datatable 2 both will merge as single
            //like col1 col2 col3
            //      1     2    3
            //      11    22    2
            //      12    232   34
            }
            catch (Exception)
            {

                throw;
            }
            
        }
