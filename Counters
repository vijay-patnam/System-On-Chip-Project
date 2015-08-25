# System-On-Chip-Project

//Displaying the sequence on the seven Segment display


//0000
//1234
//2468
//369C


module basys3(
  input clk,
   input btnC,btnU,btnL,btnR,
  input [15:0] sw,
  
  output [15:0] led,
  output [6:0] seg,
  output       dp,
  output [3:0] an
    );
    
    wire clk_d1,clk_d2;
    
   clk_div clock(
         .clk(clk),
        .rst(btnU),
       .clk_d1(clk_d1),
       .clk_d2(clk_d2)
    
        );
    
   
    
   sev_seg_disp ssd
   (
        .rst(btnU),
     .clk(clk_d1),
      .clk_d(clk_d2),
      .seven_segments(seg),
      .dot(dp),
      .anodes(an)  
     ); 
     
endmodule



+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
//////////////////////////////////////////////////////////////////////////////////////////////



module sev_seg_disp(
   input rst,
   input clk,
   input clk_d,
     
   
   output reg [6:0] seven_segments,
   output           dot,
   output   reg  [3:0] anodes  

    );

    reg  [3:0]counter_0;
   reg  [3:0]counter_1;
   reg  [3:0]counter_2;
   reg  [3:0]counter_3;

    
    reg [3:0]digit;
    reg [1:0]cnt;
    
    assign  dot=1'b1;
      
     always@(posedge clk_d)
     begin
     if(rst)
     begin
     counter_0<=4'b0;
     counter_1<=4'b0;
     counter_2<=4'b0;
     counter_3<=4'b0;
     end
     else
     begin
     counter_0<=counter_0 +1;
     counter_1<=counter_1 +2;
     counter_2<=counter_2 +3;
     counter_3<=counter_3 +4;
     end
     end
  
  
  always@(posedge clk)
  begin
      if(rst)
      cnt<=2'b0;
      
       else
        cnt<=cnt+1;
  end
  
  always@(*)
  begin
  if(cnt==2'b00)
  begin
  digit=counter_0;
  anodes=4'b0111;
  end
  else if(cnt==2'b01)
  begin
  digit=counter_1;
  anodes=4'b1011;
  end

  else if(cnt==2'b10)
  begin
  digit=counter_2;
  anodes=4'b1101;
  end

  else
  begin
  digit=counter_3;
  anodes=4'b1110;
  end
  
  
  end
    
    
   always@(*)
   begin
   case(digit)
   4'h0: seven_segments = 7'b1000000; 
   4'h1: seven_segments = 7'b1111001;
   4'h2: seven_segments = 7'b0100100;
   4'h3: seven_segments = 7'b0110000;
   4'h4: seven_segments = 7'b0011001;
   4'h5: seven_segments = 7'b0010010;
   4'h6: seven_segments = 7'b0000010;
   4'h7: seven_segments = 7'b1111000;
   4'h8: seven_segments = 7'b0000000;
   4'h9: seven_segments = 7'b0011000;
   4'hA: seven_segments = 7'b0001000;
   4'hB: seven_segments = 7'b0000011;
   4'hC: seven_segments = 7'b1000110;
   4'hD: seven_segments = 7'b0100001;
   4'hE: seven_segments = 7'b0000110;
   4'hF: seven_segments = 7'b0001110;
   
      
 endcase  
 end 
 

    
endmodule




+++++++++++++++++++++++++++++++++++++++++++++++
/////////////////////////////////////////////////////////////////////////




module clk_div(
    input clk,
    input rst,
    output clk_d1,
    output clk_d2

    );
    
    reg [29:0]counter;
    
    always@(posedge clk)
    begin
    if(rst)
    counter=30'b0;
    else
    counter<=counter+1;
    end
    
    assign clk_d2=counter[25];
    assign clk_d1=counter[15];
    
    
endmodule
