# Status-Register
module statusRegister(q,d,ld,reset,clk);
	input ld, clk, reset;
	input [3:0] d;
	output [4:0]q;
	
	reg [3:0]x;
	
	assign q = {x, d[0]};
	
	always @(posedge clk or posedge reset)begin
		
		if(reset)
			x[3:0] = 4'b0;
		else if (ld)
		   x[3:0] = d;
		else
		   x[3:0] = x;
	end
endmodule 
