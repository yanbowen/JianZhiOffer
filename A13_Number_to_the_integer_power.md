	package offer;
	
	/*
	 * 题目 ：数值的整数次方（110页）
	 * 
	 * 题目描述
	 * 		给定一个double类型的浮点数base和int类型的整数exponent。求base的exponent次方。
	 * */
	public class A13_Number_to_the_integer_power {
	
		public double Power(double base, int exponent) throws Exception {
			if (exponent == 0)
				return 1.0;
			if (base == 0.0 && exponent == 0)
				throw new Exception("base can't be 0");
			double sum = base;
			if (exponent > 0) {
				exponent = exponent - 1;
				while (exponent != 0) {
					sum = sum * base;
					exponent = exponent - 1;
				}
				return sum;
			} else {
				exponent = -exponent - 1;
				while (exponent != 0) {
					sum = sum * base;
					exponent = exponent - 1;
				}
				return 1.0 / sum;
			}
		}
	
		public double Powers(double base, int exponent) {
			int num = Math.abs(exponent);
			if (exponent == 0)
				return 1.0;
			if (exponent == 1)
				return base;
	
			double result = Powers(base, num >> 1);
			result *= result;
			if ((exponent & 0x1) == 1) {
				result *= base;
			}
			if (exponent < 0) {
				result = 1.0 / result;
			}
			return result;
		}
	}
