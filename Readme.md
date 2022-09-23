# You need to install...
* [MySql](https://dev.mysql.com/downloads/)
    * MySql Server
    * Connector/C++
* [Boost](https://www.boost.org/doc/libs/1_72_0/more/getting_started/windows.html)

# Installation

## Boost

![image](https://user-images.githubusercontent.com/36888398/191958803-fe2be779-8828-4bbb-b7d3-24522065210e.png)

You run **bootstrap.bat**. (bootstrap.bat 파일을 실행합니다.)

And when **b2.exe** is created.. run. (b2.exe 파일이 생성되면 이 녀석도 실행합니다.)

check the "stage" folder has been created. (stage 폴더가 생겼는지 확인합니다.)

## Visual Studio C++ Project

![image](https://user-images.githubusercontent.com/36888398/191959478-c40bad9a-91b5-470b-b173-f9019a89a57b.png)

[Configuration Properties] - [C/C++] - [General] - [Additional Include Directories]

Add that folder path. (사진 속 폴더 경로를 추가합니다.)

![image](https://user-images.githubusercontent.com/36888398/191959699-4973d2db-8b27-4a10-afe7-a6cb1e63699d.png)

[Configuration Properties] - [Linker] - [General] - [Additional Library Directories]

Add that folder path. (사진 속 폴더 경로를 추가합니다.)

![image](https://user-images.githubusercontent.com/36888398/191959822-5eb526c1-ca2c-42a4-a81b-fc2b90ba8f75.png)

Add that library. (라이브러리를 추가합니다.)

## Copy and Paste

![image](https://user-images.githubusercontent.com/36888398/191960016-80852648-d297-4539-8ebf-8720375c453c.png)

Copy four dll files. (4개의 파일을 복사합니다.)

![image](https://user-images.githubusercontent.com/36888398/191960171-0cd37823-9156-46cb-8d12-faf3b81bf506.png)

Paste in your project path. (프로젝트 경로에 붙여넣기 합니다.)

## Example

```cpp
#include <stdlib.h>
#include <iostream>

#include <jdbc/cppconn/driver.h>
#include <jdbc/cppconn/exception.h>
#include <jdbc/cppconn/resultset.h>
#include <jdbc/cppconn/statement.h>

int main() {
	sql::Driver *driver;
	sql::Connection *con;

        // Connect to the MySQL
	driver = get_driver_instance();
	con = driver->connect("host", "user", "password");

        // Connect to the MySQL #### database
	/* con->setSchema("####"); */

	if (!con) {
		printf("Failed!\n");
	}
	else {
		printf("Successful!\n");
	}

	delete con;
	
	return 0;
}
```
`Result: Successful or Failed`

if you get the error message. (std::bad_alloc at memory location) (만약, std::bad_alloc at memory location 오류 메시지가 나타난다면)

change configuration. [Debug --> Release] (빌드 모드를 Debug에서 Release로 변경합니다.)
