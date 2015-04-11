/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

package data.mining;

import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

/**
 *
 * @author sahil
 */
public class DataMining {

    public static void main(String[] args) throws FileNotFoundException {
        String fileName = "/Users/sahil/Documents/Sahil_Study/NYU/Data_Mining/naive.csv";
        float global_th=0, global_acc=0, global_hh=0, global_hs=0;
        Scanner sc = new Scanner(new File(fileName));
        String[][] data = new String[2757][4];
        for(int i=0;i<2757;i++)
        {
            String[] arr = (sc.nextLine()).split(",");
            for(int j=0;j<4;j++)
            {
                data[i][j] = arr[j];
            }
        }
        
        double th;
        
        float[] acc = new float[51];
        float[] hh = new float[51];
        float[] hs = new float[51];//ham but predicted as spam
        float[] ss = new float[51];
        float[] sh = new float[51];
        float[] th_graph = new float[51];
        int k = 0;
        for(th = 0.00; th<=1.00;th = th+.02)
        {
            float correct = 0;
            float hh_count = 0;
            float sh_count = 0;
            float hs_count = 0;//ham but predicted as spam
            float ss_count = 0;
            
            // probability of a ham at 2 and probability of spam at column 3.
            // Actual = 0, predicted = 1
            // th is threshold for Ham. If probability of ham > th, we predict it as ham
            for(int i=0;i<2757;i++)
            {
           //     System.out.println(data[i][2]);
                if((data[i][2]).contains("*"))
                {    
                    int temp = data[i][2].indexOf("*");
                    data[i][2] = data[i][2].substring(temp+1);
         //           System.out.println(data[i][2]);
                }
                if(Float.parseFloat(data[i][2]) > th)
                {
                    if(data[i][0].equals("ham"))
                        hh_count++;
                    else
                        sh_count++;
                }
                else
                {
                    if(data[i][0].equals("spam"))
                        ss_count++;
                    else
                        hs_count++;
                }
            }
            hh[k] = hh_count;
            sh[k] = sh_count;
            hs[k] = hs_count;
            ss[k] = ss_count;
            acc[k] = (hh_count + ss_count) / 2757;
            th_graph[k] = (float) th;
            if(acc[k]>global_acc)
            {
                global_acc=acc[k];
                global_th = (float) th;
            }
            if(k==30)
            {
                System.out.println(th + "\n" + hh[k] + " " + sh[k] + "\n" + hs[k] + " " + ss[k]);
            }
            k++;
        }
        //System.out.println(global_acc + " " + global_th);
        for(int p = 0 ; p<51;p++)
        {
            System.out.println(th_graph[p] + " " + acc[p] + " " + hh[p] + " " + hs[p]);
        }
    }
    
}
