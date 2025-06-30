# clock_using_verilg
module digital_clk(output reg [59:0]sec,output reg [59:0]min,
 output reg [23:0]hour,input clk,rst

    );
   reg day=0;
    always @(posedge clk) begin
    if(rst)
    begin
    sec=2'd0;
    min=2'd0;
    hour=2'd0;
    end
    else
    begin
    sec=sec+1;
    if(sec>60)
    begin
    min=min+1;
    sec=2'd0;
    end
   if(min>60) begin
   hour=hour+1;
   min=2'd0;
   end
   if(hour>24) begin
   day=day+1;
   hour=2'd0;
   end
    end
    end
endmodule
