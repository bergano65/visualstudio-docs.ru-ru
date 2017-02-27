---
title: "Пример Demo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "анализ кода, примеры"
  - "пример [Visual Studio ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# Пример Demo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В следующих процедурах демонстрируется создание образца для раздела [Пошаговое руководство. Проверка кода C\/C\+\+ на наличие дефектов](../Topic/Walkthrough:%20Analyzing%20C-C++%20Code%20for%20Defects.md).  В процедурах создаются следующие объекты:  
  
-   решение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с именем CppDemo;  
  
-   проект статической библиотеки с именем CodeDefects;  
  
-   проект статической библиотеки с именем Annotations.  
  
 В процедурах также предусмотрен код для заголовка и CPP\-файлов статических библиотек.  
  
### Создание решения CppDemo и проекта CodeDefects  
  
1.  В меню **Файл** последовательно выберите пункты **Создать**, **Новый проект**.  
  
2.  Если Visual C\+\+ не используется в VS в качестве языка по умолчанию, разверните в списке дерева **Типы проектов** узел **Другие языки**.  
  
3.  Разверните узел **Visual C\+\+** и выберите **Общие**.  
  
4.  В поле **Шаблоны** выберите **Пустой проект**.  
  
5.  В текстовом поле **Имя** введите **CodeDefects**.  
  
6.  Установите флажок **Создать каталог для решения**.  
  
7.  В текстовом поле **Имя решения** введите **CppDemo**.  
  
### Настройка проекта CodeDefects в качестве статической библиотеки  
  
1.  Щелкните правой кнопкой проект **CodeDefects** в обозревателе решений и выберите пункт **Свойства**.  
  
2.  Разверните узел **Свойства конфигурации** и выберите **Общие**.  
  
3.  В списке **Общие** выберите текст в столбце рядом с надписью **Конечное расширение**, а затем введите **.lib**.  
  
4.  В области **Значения по умолчанию для проекта** щелкните столбец рядом с надписью **Тип конфигурации**, а затем выберите **Статическая библиотека \(.lib\)**.  
  
### Добавление заголовка и файла исходного кода в проект CodeDefects  
  
1.  В обозревателе решений разверните узел **CodeDefects**, щелкните правой кнопкой мыши папку **Заголовочные файлы** и последовательно выберите пункты **Добавить** и **Новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выделите поле **Код** и выберите **Заголовочный файл \(.h\)**.  
  
3.  В окне **Имя** введите **Bug.cpp** и нажмите кнопку **Добавить**.  
  
4.  Скопируйте приведенный ниже код и вставьте его в файл **Bug.cpp** в редакторе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  В обозревателе решений щелкните правой кнопкой мыши папку **Файлы исходного кода** и последовательно выберите пункты **Создать** и **Новый элемент**.  
  
6.  В диалоговом окне **Добавление нового элемента** выберите вариант **Файл C\+\+ \(.cpp\)**.  
  
7.  В окне **Имя** введите **Bug.cpp** и нажмите кнопку **Добавить**.  
  
8.  Скопируйте приведенный ниже код и вставьте его в файл Bug.h в редакторе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Откройте меню **Файл**, а затем выберите команду **Сохранить все**.  
  
### Добавление проекта Annotations и настройка его в качестве статической библиотеки  
  
1.  В обозревателе решений щелкните правой кнопкой мыши папку **CppDemo** и последовательно выберите пункты **Добавить** и **Новый проект**.  
  
2.  В диалоговом окне **Добавить новый проект** разверните узел Visual C\+\+ и последовательно выберите **Общие**, **Пустой проект**.  
  
3.  В текстовом поле **Имя** введите **Annotations** и нажмите кнопку **Добавить**.  
  
4.  Щелкните правой кнопкой проект **Annotations** в обозревателе решений и выберите пункт **Свойства**.  
  
5.  Разверните узел **Свойства конфигурации** и выберите **Общие**.  
  
6.  В списке **Общие** выберите текст в столбце рядом с надписью **Конечное расширение**, а затем введите **.lib**.  
  
7.  В области **Значения по умолчанию для проекта** щелкните столбец рядом с надписью **Тип конфигурации**, а затем выберите **Статическая библиотека \(.lib\)**.  
  
### Добавление заголовочного файла и файла исходного кода в проект Annotations  
  
1.  В обозревателе решений разверните узел **Annotations**, щелкните правой кнопкой мыши папку **Заголовочные файлы** и последовательно выберите пункты **Добавить** и **Новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выберите вариант **Заголовочный файл \(.h\)**.  
  
3.  В окне **Имя** введите **annotations.h** и нажмите кнопку **Добавить**.  
  
4.  Скопируйте приведенный ниже код и вставьте его в файл **annotations.h** в редакторе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  В обозревателе решений щелкните правой кнопкой мыши папку **Файлы исходного кода** и последовательно выберите пункты **Создать** и **Новый элемент**.  
  
6.  В диалоговом окне **Добавление нового элемента** выделите поле **Код** и выберите **Файл C\+\+ \(.cpp\)**.  
  
7.  В окне **Имя** введите **annotations.cpp** и нажмите кнопку **Добавить**.  
  
8.  Скопируйте приведенный ниже код и вставьте его в файл **annotations.cpp** в редакторе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Откройте меню **Файл**, а затем выберите команду **Сохранить все**.