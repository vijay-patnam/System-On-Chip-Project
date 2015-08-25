# System-On-Chip-Project


module sev_seg_disp(

   input  [3:0]digit,
   input      single_digit,
   input      show_dot,
   
   output reg [6:0] seven_segments,
   output           dot,
   output     [3:0] anodes  

    );
    
   always@(*)
   begin
   case(digit)
   4'h0: seven_segments = 7'b0001001; //modified to display H
   4'h1: seven_segments = 7'b1000111;//modified to display L
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
 
 assign dot =~show_dot;
 assign anodes = single_digit?4'b1110:4'b0000;
    
endmodule






+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

//////////////////////////////////////////////////////////////////////////////////




module basys3(
  input clk,
   input btnC,btnU,btnL,btnR,
  input [15:0] sw,
  
  output [15:0] led,
  output [6:0] seg,
  output       dp,
  output [3:0] an
    );
    
    wire [3:0]digit;
    
    assign digit= (sw[0])?4'b0000:4'b0001;
    
   sev_seg_disp single_digit_display
   (
       .digit(digit),
      .single_digit (1'b1),
      .show_dot    (sw[14]),
      
      .seven_segments (seg),
      .dot (dp),
      .anodes (an)
   
     ); 
     
     endmodule

