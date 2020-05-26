# Hackathon_coding

import java.util.*;
import java.io.*;
import java.text.DecimalFormat;
import java.math.RoundingMode;
import java.io.FileNotFoundException;
import org.json.JSONObject;
public class Sample {

	public static void main(String[] args) throws IOException 
	{
		double[] arr = new double[10000];
		JSONObject a  = new JSONObject();
		JSONObject b = new JSONObject();
		File f = new File("C:\\Users\\admin\\Desktop\\Memory.txt");
		try (BufferedReader bf = new BufferedReader(new FileReader(f))) 
        {
            String readLine;
            double temp;
            
            int line = 0;
            int i=0;
            double sum=0.0;
            double max = 0.0;
            while ((readLine = bf.readLine()) != null) 
            {
                if (line % 2 != 0) {
                	
                	String str=readLine;
                	str=str.replaceAll("[^0-9]","");
                    str=str.trim();
                    
                    //System.out.println(str);
                    temp=Integer.parseInt(str);
                   
                    arr[i++]=temp/10000;
                    
                }
                line++;
            }
            String str1;
            for(int j=0;j<938;j++)
            {
            	str1 = String.format("%d",j);
            	a.put(str1 + "s", arr[j]);
            	if(max<arr[j])
            		max=arr[j];
            	sum=sum+arr[j];
            }
            //System.out.println(a);
            double average=sum/938;
            DecimalFormat df = new DecimalFormat("#.###");
            df.setRoundingMode(RoundingMode.CEILING);
            a.put("AverageMemory(MB)", df.format(average));
            a.put("values: ", b);
            a.put("MaximumMemory(MB)", df.format(max));
            System.out.println(a);
         }
 }
}

