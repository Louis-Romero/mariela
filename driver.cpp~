#include <iostream>
#include <fstream>
#include <cstdlib>
#include <cmath>
#include <iomanip>

using namespace std;

void mean(double aryA[], double aryR[], double counterA, double counterR, double& meanA, double& meanR);
void var(double aryA[],double aryR[], double counterA, double counterR, double meanA, double meanR, double& sampleVarianceA, double& sampleVarianceR);
void stdDev(double sampleVarianceA, double sampleVarianceR, double& standardDeviationA, double& standardDeviationR);
double avgPower(double aryA[], double aryR[], double counterA, double counterR, double& averagePowerA, double& averagePowerR);
double avgMagnitude(double aryA[], double aryR[], double counterA, double counterR, double& averageMagnitudeA, double& averageMagnitudeR);
double zeroCross(double aryA[], double aryR[], double counterA, double counterR, double& zeroCrossCounterA, double& zeroCrossCounterR);


int main()
{
    const int SIZE = 5000;
    double arrayOfActualTwoA[SIZE];
    double arrayOfRecordingTwoB[SIZE];
    ifstream fin_two_a, fin_two_b;
    ofstream fout_results;
    double counterActual = 0, counterRecording = 0; 
    double meanActual, meanRecording, sampleVarianceActual, sampleVarianceRecording, standardDeviationActual, standardDeviationRecording;
    double averagePowerActual, averagePowerRecording, averageMagnitudeActual, averageMagnitudeRecording;
    double zeroCrossCounterActual = 0, zeroCrossCounterRecording = 0;
    double percentDiffMean, percentDiffVariance, percentDiffStandardDev, percentDiffAvgPower, percentDiffAvgMagnitude, percentDiffZeroCross; 
    
    //Opening of two data files and output file
    fin_two_a.open("two_a.txt");
    fin_two_b.open("two_b.txt");
    fout_results.open("comparison.txt");
    
    //File open error checking
    if(fin_two_a.fail()|| fin_two_b.fail()|| fout_results.fail())
    {
        cout << "Error opening file!" << endl;
        exit(1);
    }
    
    //Filling array actual data
    for(int ix = 0; ix < 5000; ix++)
    { 
        fin_two_a >> arrayOfActualTwoA
     [ix];
     counterActual++;  
    }
    
    //Filling array recording data
    for(int ix = 0; ix < 5000; ix++)
    { 
        fin_two_b >> arrayOfRecordingTwoB
     [ix];  
     counterRecording++;
    }
    //Passing through function to find mean
    mean(arrayOfActualTwoA, arrayOfRecordingTwoB, counterActual, counterRecording, meanActual, meanRecording); 
    
    //I now have two different means
    //meanActual and meanRecording
    
    //Pass meanActual and meanRecording through variance function to determine sampleVarianceActual and sampleVarianceRecording
    var(arrayOfActualTwoA,arrayOfRecordingTwoB, counterActual, counterRecording, meanActual, meanRecording, sampleVarianceActual, sampleVarianceRecording);
    
    //I now have two sample variances
    //sampleVarianceActual and sampleVarianceRecording
    stdDev(sampleVarianceActual, sampleVarianceRecording, standardDeviationActual, standardDeviationRecording);
    
    //I now have two standard deviations
    //standardDeviationActual and standardDeviationRecording
    avgPower(arrayOfActualTwoA, arrayOfRecordingTwoB, counterActual, counterRecording, averagePowerActual, averagePowerRecording);
    
    //I now have two average powers
    //averagePowerActual and averagePowerRecording
    
    avgMagnitude(arrayOfActualTwoA, arrayOfRecordingTwoB, counterActual, counterRecording, averageMagnitudeActual, averageMagnitudeRecording);
    
    //I now have two average magnitudes
    //averageMagnitudeActual and averageMagnitudeRecording
    
    zeroCross(arrayOfActualTwoA, arrayOfRecordingTwoB, counterActual, counterRecording, zeroCrossCounterActual, zeroCrossCounterRecording);

    //I now have two counts of zero cross
    //zeroCrossCounterActual and zeroCrossCounterRecording
    percentDiffMean = (fabs(meanRecording -meanActual) / meanActual) * 100;
    percentDiffVariance = (fabs(sampleVarianceRecording - sampleVarianceActual) / sampleVarianceActual) * 100;
    percentDiffStandardDev = (fabs(standardDeviationRecording - standardDeviationActual) / standardDeviationActual) * 100;
    percentDiffAvgPower = (fabs(averagePowerRecording - averagePowerActual) / averagePowerActual) * 100;
    percentDiffAvgMagnitude = (fabs(averageMagnitudeRecording - averageMagnitudeActual) / averageMagnitudeActual) * 100;
    percentDiffZeroCross = (fabs(zeroCrossCounterRecording -zeroCrossCounterActual) / zeroCrossCounterActual) * 100;
    
    fout_results << "Team Member: Louis Paul Romero" << endl;
  
    fout_results.setf(ios::left);
    fout_results << endl;
    fout_results << setw(20) << " " << setw(20) << "two_a.txt" << setw(20) << "two_b.txt" << setw(20) << "% difference" << endl;
   fout_results << setw(20) << "Mean" << setw(20) << meanActual << setw(20) << meanRecording << setw(20) << percentDiffMean << endl;
   fout_results << setw(20) << "Variance" << setw(20) << sampleVarianceActual << setw(20) << sampleVarianceRecording << setw(20) << percentDiffVariance << endl;
   fout_results << setw(20) << "Standard Deviation" << setw(20) << standardDeviationActual << setw(20) << standardDeviationRecording << setw(20) << percentDiffStandardDev << endl;
   fout_results << setw(20) << "Average Power" << setw(20) << averagePowerActual << setw(20) << averagePowerRecording << setw(20) << percentDiffAvgPower << endl;
   fout_results << setw(20) << "Average Magnitude" << setw(20) << averageMagnitudeActual << setw(20) << averageMagnitudeRecording << setw(20) << percentDiffAvgMagnitude << endl;
   fout_results << setw(20) << "Zero Cross" << setw(20) << zeroCrossCounterActual << setw(20) << zeroCrossCounterRecording << setw(20) << percentDiffZeroCross << endl;
   
//Which values for each data file match most closely? 
//Mean, variance, standard deviation, average power had a percent difference of less than 10 percent.
//Which values for each data file are most different?
//Average magnitude and zero cross had a percent difference from 20 percent through 39 percent.  
//Are there other statistical measures that you could suggest?
//Not really sure.  
//Can you determine if these sound recordings are from the same person? Explain.
//Despite the high percent difference of the average magnitude and zero cross, I conclude that the audio recordings are a match.  I wonder what acceptable ranges are for this field of work to make such determination.
          
    fin_two_a.close();
    fin_two_b.close();
    fout_results.close();
    return 0;
}

void mean(double aryA[],double aryR[], double counterA, double counterR, double& meanA, double& meanR)
{
    double sum = 0;
    
     for(int ix = 0; ix < counterA; ix++)
    { 
        sum += aryA[ix];
    }
    meanA = sum/counterA;
    
    sum = 0;
    
    for(int ix = 0; ix < counterR; ix++)
    { 
        sum += aryR[ix];
    }
    meanR = sum/counterR;       
}

void var(double aryA[],double aryR[], double counterA, double counterR, double meanA, double meanR, double& sampleVarianceA, double& sampleVarianceR)
{
    double sumForVariance = 0;
    double denominatorForVarianceA, denominatorForVarianceR;
    
    for(int ix = 0; ix < counterA; ix++)
    { 
        sumForVariance += pow((aryA[ix]- meanA), 2);
    }
    
    denominatorForVarianceA = counterA - 1;
    sampleVarianceA = sumForVariance/denominatorForVarianceA;
    
    sumForVariance = 0;

    for(int ix = 0; ix < counterR; ix++)
    { 
        sumForVariance += pow((aryR[ix]- meanR), 2);
    }
    denominatorForVarianceR = counterR - 1;
    sampleVarianceR = sumForVariance/denominatorForVarianceR;        
}

void stdDev(double sampleVarianceA, double sampleVarianceR, double& standardDeviationA, double& standardDeviationR)
{
    standardDeviationA = sqrt(sampleVarianceA);
    standardDeviationR = sqrt(sampleVarianceR);    
}

double avgPower(double aryA[], double aryR[], double counterA, double counterR, double& averagePowerA, double& averagePowerR)
{
    double sumActual = 0, sumRecording = 0;

    for(int ix = 0; ix < counterA; ix++)
    {
        sumActual += pow(aryA[ix], 2);
    }
    averagePowerA = sumActual/counterA;
    
    for(int ix = 0; ix < counterR; ix++)
    {
        sumRecording += pow(aryR[ix], 2);
    }
    averagePowerR = sumRecording/counterR;
}

double avgMagnitude(double aryA[], double aryR[], double counterA, double counterR, double& averageMagnitudeA, double& averageMagnitudeR)
{
    double sumActual = 0, sumRecording = 0;
    
    for(int ix = 0; ix < counterA; ix++)
    {
        sumActual += fabs(aryA[ix]);
    }
    averageMagnitudeA = sumActual/counterA;
    
    for(int ix = 0; ix < counterR; ix++)
    {
        sumRecording += fabs(aryR[ix]);
    }
    averageMagnitudeR = sumRecording/counterR; 
}
    
double zeroCross(double aryA[], double aryR[], double counterA, double counterR, double& zeroCrossCounterA, double& zeroCrossCounterR)
{
    for(int ix = 0; ix < counterA -1; ix++)
    {
        if((aryA[ix] * aryA[ix + 1]) < 0)
        {
            zeroCrossCounterA++;
        } 
    }
    
    for(int ix = 0; ix < counterR - 1; ix++)
    {
        if((aryR[ix] * aryR[ix + 1]) < 0)
        {
            zeroCrossCounterR++;
        } 
    }
}
