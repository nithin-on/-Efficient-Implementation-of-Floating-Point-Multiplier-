# -Efficient-Implementation-of-Floating-Point-Multiplier-
module floating_point_multiplier( 
input wire [31:0] a, 
input wire [31:0] b, 
output reg [31:0] result
);
wire sign_a = a[31]; 
wire [7:0] exponent_a = a[30:23]; 
wire [22:0] mantissa_a = a[22:0]; 
wire sign_b = b[31]; 
wire [7:0] exponent_b = b[30:23]; 
wire [22:0] mantissa_b = b[22:0]; 
wire sign_result = sign_a ^ sign_b; 
wire [7:0] exponent_result;
wire [23:0] mantissa_result; 
wire [46:0] mantissa_mult; 
assign mantissa_mult = {mantissa_a, 23'b0} {mantissa_b, 23'b0}; 
assign exponent_result = exponent_a + exponent_b 127;
assign mantissa_result = mantissa_mult[46:24]; 
always @(*) begin 
result[31] = sign_result; 
result[30:23] = exponent_result; 
result [22:0] = mantissa_result[22:0]; 
end
endmodule 
