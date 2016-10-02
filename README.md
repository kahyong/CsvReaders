package com.hr.utils;

import java.nio.charset.Charset;

import org.springframework.context.support.ClassPathXmlApplicationContext;

import com.csvreader.CsvReader;
import com.hr.interfaces.UserService;


public class CsvReaders {
	private static ClassPathXmlApplicationContext ctx;
	private static  UserService userService;

	public static ClassPathXmlApplicationContext getContext() {
		return ctx;
	}


	public static void main(String args[]) {
		ctx= new ClassPathXmlApplicationContext("classpath:/conf/spring/applicationContext.xml");
		userService = (UserService) ctx.getBean("userService");
		try {
		
		 CsvReader r = new CsvReader("/Users/chongkahyong/Desktop/file.csv",',',Charset.forName("UTF-8"));
         //读取表头
		 r.readHeaders();
  int test=0;
          //逐条读取记录，直至读完
          while (r.readRecord()) {
        	  test++;
              //读取一条记录
//              System.out.println(r.getRawRecord());
//        	  userService.userLogintest(r.get("name").toString(), r.get("email").toString(), r.get("phone").toString());
              //按列名读取这条记录的值
//             System.out.println(r.get("name"));
//             System.out.println(r.get("email"));
//             System.out.println(r.get("phone"));
//             54
         }
         r.close();
         System.out.println(test);
		} catch (Exception e) {
			// TODO: handle exception
		}
		
	}
}
