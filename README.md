# utl-getting-rid-of-carriage-returns-embedded-in-a-text-files
Getting Rid of Carriage Returns Embedded in a Text Files 

    Getting Rid of Carriage Returns Embedded in a Text Files                                                                                 
                                                                                                                                             
    If the number of '|' characters in a record is constant, 4 in this solution.                                                             
                                                                                                                                             
    github                                                                                                                                   
    https://tinyurl.com/y5t32bvx                                                                                                             
    https://github.com/rogerjdeangelis/utl-getting-rid-of-carriage-returns-embedded-in-a-text-files                                          
                                                                                                                                             
    SAS Forum                                                                                                                                
    https://tinyurl.com/y38dnw2w                                                                                                             
    https://communities.sas.com/t5/SAS-Programming/Getting-Rid-of-Carriage-Returns-Embedded-in-a-Text-txt-Files/m-p/557564/highlight/true#M15
                                                                                                                                             
    *_                   _                                                                                                                   
    (_)_ __  _ __  _   _| |_                                                                                                                 
    | | '_ \| '_ \| | | | __|                                                                                                                
    | | | | | |_) | |_| | |_                                                                                                                 
    |_|_| |_| .__/ \__,_|\__|                                                                                                                
            |_|                                                                                                                              
    ;                                                                                                                                        
                                                                                                                                             
    * Save a file with imbeded 'ODOA'x (CRLFs);                                                                                              
    * this is what the file will look like in notepad or a SAS editor;                                                                       
                                                                                                                                             
    filename ft15f001 "d:/txt/flo.txt";                                                                                                      
    parmcards4;                                                                                                                              
    1|1|1|1|1                                                                                                                                
    2|2|                                                                                                                                     
    2|2|2                                                                                                                                    
    3|3|3|                                                                                                                                   
    3|3                                                                                                                                      
    4|4|4|4|4                                                                                                                                
    ;;;;                                                                                                                                     
    run;quit;                                                                                                                                
                                                                                                                                             
    *            _               _                                                                                                           
      ___  _   _| |_ _ __  _   _| |_                                                                                                         
     / _ \| | | | __| '_ \| | | | __|                                                                                                        
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                         
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                        
                    |_|                                                                                                                      
    ;                                                                                                                                        
                                                                                                                                             
    Up to 40 obs from WANT total obs=4                                                                                                       
                                                                                                                                             
    Obs    P1    P2    P3    P4    P5     NEWTXT                                                                                             
                                                                                                                                             
     1     1     1     1     1     1     1|1|1|1|1                                                                                           
     2     2     2     2     2     2     2|2|2|2|2                                                                                           
     3     3     3     3     3     3     3|3|3|3|3                                                                                           
     4     4     4     4     4     4     4|4|4|4|4                                                                                           
                                                                                                                                             
                                                                                                                                             
    d:/txt/floOut.txt                                                                                                                        
                                                                                                                                             
    1|1|1|1|1                                                                                                                                
    2|2|2|2|2                                                                                                                                
    3|3|3|3|3                                                                                                                                
    4|4|4|4|4                                                                                                                                
                                                                                                                                             
    *                                                                                                                                        
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                       
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                                      
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                                      
    | .__/|_|  \___/ \___\___||___/___/                                                                                                      
    |_|                                                                                                                                      
    ;                                                                                                                                        
                                                                                                                                             
    data want;                                                                                                                               
      informat p1-p5 $char1.;                                                                                                                
      infile "d:/txt/flo.txt" delimiter="|";                                                                                                 
      file "d:/txt/floOut.txt" ;                                                                                                             
      input p1-p5  ;                                                                                                                         
      newTxt=catx('|',of P:);                                                                                                                
      put newTxt;                                                                                                                            
      putLog newTxt;                                                                                                                         
    run;quit;                                                                                                                                
                                                                                                                                             
