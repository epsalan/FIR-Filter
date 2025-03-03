`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date: 04.02.2024 12:43:55
// Design Name: 
// Module Name: ScalableMicroprogrammedFIR_tb
// Project Name: 
// Target Devices: 
// Tool Versions: 
// Description: 
// 
// Dependencies: 
// 
// Revision:
// Revision 0.01 - File Created
// Additional Comments:
// 
//////////////////////////////////////////////////////////////////////////////////


module ScalableMicroprogrammedFIR_tb;

  // Parameters for the filter
  parameter M = $clog2(256); // Maximum array size

  // Inputs
  reg clk;
  reg reset;
  reg start;
  reg [7:0] input_data;
  reg [7:0] coefficients;
  reg [7:0] N_input;

  // Output
  wire [15:0] output_result;

  // Instantiate the module
  ScalableMicroprogrammedFIR uut (
    .clk(clk),
    .reset(reset),
    .start(start),
    .input_data(input_data),
    .coefficients(coefficients),
    .N_input(N_input),
    .output_result(output_result)
  );

  // Clock generation
  initial begin
    clk = 0;
    forever #5 clk = ~clk;
  end

  // Testbench stimulus
  initial begin
    reset = 1;
    start = 0;
    input_data = 8'h00;
    coefficients = 8'h00;
    N_input = 8'h01;

    // Apply reset
    #10 reset = 0;

    // Test case 1: N_input = 1, single tap filter
    #10 start = 1;
    #10 input_data = 8'h0A;
    #10 coefficients = 8'h03;
    #10 N_input = 8'h01;

    // Test case 2: N_input = 2, two tap filter
    #100 start = 1;
    #10 input_data = 8'h0F;
    #10 coefficients = 8'h01;
    #10 N_input = 8'h02;

    // Test case 3: N_input = 3, three tap filter
    #100 start = 1;
    #10 input_data = 8'h05;
    #10 coefficients = 8'h02;
    #10 N_input = 8'h03;

    // Test case 4: N_input = 4, four tap filter
    #100 start = 1;
    #10 input_data = 8'h07;
    #10 coefficients = 8'h01;
    #10 N_input = 8'h04;

    // End of test cases
    #100 $finish;
  end

  // Monitor
  always @(posedge clk) begin
    $display("Time=%0t, output_result=%h", $time, output_result);
  end

endmodule
