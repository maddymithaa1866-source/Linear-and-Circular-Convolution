# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 

// Linear Convolution
clc;
clear;
clf;

// === OPTION 1: Take input from user ===
// IMPORTANT: Enter sequences inside square brackets like [1 2 3]
//x = input("Enter x(n) : ");
//h = input("Enter h(n) : ");

// === OPTION 2: Predefined test sequences ===
x = [1 2 3];
h = [4 5 6];

// Lengths
Nx = length(x);
Nh = length(h);
Ny = Nx + Nh - 1;

// Zero padding
x_p = [x, zeros(1, Ny - Nx)];
h_p = [h, zeros(1, Ny - Nh)];

// Output initialization
y = zeros(1, Ny);

// Convolution (without using conv)
for n = 0:Ny-1
    for k = 0:Nx-1
        if (n-k >= 0 & n-k < Nh) then
            y(n+1) = y(n+1) + x_p(k+1) * h_p(n-k+1);
        end
    end
end

// Display result
disp("y(n) = ");
disp(y);

// === Plotting ===
subplot(3,1,1);
n1 = 0:Nx-1;
plot2d3(n1, x);
title("x(n)");

subplot(3,1,2);
n2 = 0:Nh-1;
plot2d3(n2, h);
title("h(n)");

subplot(3,1,3);
n3 = 0:Ny-1;
plot2d3(n3, y);
title("y(n) = x(n) * h(n)");


## PROGRAM (Circular Convolution): 

// Circular Convolution 
clc; clear;
x=[1 1 1 1];
n1=0:1:length(x)-1;
subplot(3,1,1);
plot2d3(n1,x);
xlabel('time');
ylabel('amplitude');
title('input sequence');
h=[1 2 3];
n2=0:1:length(h)-1;
subplot(3,1,2);
plot2d3(n2,h);
xlabel('time');
ylabel('amplitude');
title('impulse sequence');
N1=length(x);
N2=length(h);
N=max(N1,N2);
N3=N1-N2;
if(N3>0)
h=[h,zeros(1,N3)];
else
x=[x,zeros(1,abs(N3))];
end
disp(x)
disp(h)
for n=1:N
y(n)=0;
for i=1:N
j=n-i+1;
if(j<=0)
j=N+j;
end
y(n)=y(n)+x(i)*h(j);
end
end
disp(y)
n=0:N-1;
subplot(3,1,3);
plot2d3(n,y);
xlabel('time');
ylabel('amplitude');
title('circular convolution');


## OUTPUT (Linear Convolution): <img width="765" height="725" alt="image" src="https://github.com/user-attachments/assets/dad45edb-13d9-4ecc-8d86-0a84eddbaba8" />


## OUTPUT (Circular Convolution): <img width="765" height="725" alt="image" src="https://github.com/user-attachments/assets/18a28a97-6bc4-4111-97af-4550024f68c9" />


## RESULT: Thus got the output for both linear and circular convolution
