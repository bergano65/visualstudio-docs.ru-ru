---
title: Демонстрация примера | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 284bee5cc12a7fd4f1e6c038fdd377d8cd1f8cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="demo-sample"></a>Пример Demo
Это следующие процедуры демонстрируют Создание образца для [Пошаговое руководство: анализ кода C/C++ для дефекта](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Процедуры создания:  
  
-   Объект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решение с именем CppDemo.  
  
-   Проекта статической библиотеки с именем CodeDefects.  
  
-   Проекта статической библиотеки с именем заметок.  
  
 В процедурах также предусмотрен код для заголовка и CPP-файлов статических библиотек.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Создайте CppDemo решение и проект CodeDefects  
  
1.  Нажмите кнопку **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **новый проект**.  
  
2.  В **типов проектов** дереве списка, если Visual C++ не языка по умолчанию в Visual STUDIO разверните **другие языки**.  
  
3.  Разверните **Visual C++**, а затем нажмите кнопку **Общие**.  
  
4.  В **шаблоны**, нажмите кнопку **пустой проект**.  
  
5.  В **имя** введите **CodeDefects**.  
  
6.  Выберите **создать каталог для решения** флажок.  
  
7.  В **имя решения** введите **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Настройка проекта CodeDefects в качестве статической библиотеки  
  
1.  В обозревателе решений щелкните правой кнопкой мыши **CodeDefects** и нажмите кнопку **свойства**.  
  
2.  Разверните **свойства конфигурации** и нажмите кнопку **Общие**.  
  
3.  В **Общие** выберите текст в столбце рядом с **Конечное расширение**, а затем введите **.lib**.  
  
4.  В **проекта по умолчанию**, щелкните столбец рядом с **тип конфигурации**, а затем нажмите кнопку **статическая библиотека (.lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Добавьте файл заголовка и исходный проект CodeDefects  
  
1.  В обозревателе решений откройте **CodeDefects**, щелкните правой кнопкой мыши **файлы заголовков**, нажмите кнопку **добавить**, а затем нажмите кнопку **новый элемент**.  
  
2.  В **Добавление нового элемента** диалоговое окно, нажмите кнопку **кода**, а затем нажмите кнопку **заголовочный файл (.h)**.  
  
3.  В **имя** введите **Bug.cpp** и нажмите кнопку **добавить**.  
  
4.  Скопируйте следующий код и вставьте его в **Bug.cpp** файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактора.  
  
    ```cpp
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
  
5.  В обозревателе решений щелкните правой кнопкой мыши **исходные файлы**, пункты **New**, а затем нажмите кнопку **новый элемент**.  
  
6.  В **Добавление нового элемента** диалоговое окно, нажмите кнопку **файл C++ (.cpp)**  
  
7.  В **имя** введите **Bug.cpp** и нажмите кнопку **добавить**.  
  
8.  Скопируйте следующий код и вставьте его в файл Bug.h в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактора.  
  
    ```cpp
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
  
9. Нажмите кнопку **файл** меню, а затем нажмите **сохранить все**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Добавление проекта Annotations и настройте его в качестве статической библиотеки  
  
1.  В обозревателе решений щелкните **CppDemo**, пункты **добавить**, а затем нажмите кнопку **новый проект**.  
  
2.  В **Добавление нового проекта** диалогового окна разверните Visual C++, нажмите кнопку **Общие**, а затем нажмите кнопку **пустой проект**.  
  
3.  В **имя** введите **заметки**, а затем нажмите кнопку **добавить**.  
  
4.  В обозревателе решений щелкните правой кнопкой мыши **заметки** и нажмите кнопку **свойства**.  
  
5.  Разверните **свойства конфигурации** и нажмите кнопку **Общие**.  
  
6.  В **Общие** выберите текст в столбце рядом с **Конечное расширение**, а затем введите **.lib**.  
  
7.  В **проекта по умолчанию**, щелкните столбец рядом с **тип конфигурации**, а затем нажмите кнопку **статическая библиотека (.lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Добавьте файл заголовка и исходный файл в проект заметок  
  
1.  В обозревателе решений откройте **заметки**, щелкните правой кнопкой мыши **файлы заголовков**, нажмите кнопку **добавить**и нажмите кнопку **новый элемент**.  
  
2.  В **Добавление нового элемента** диалоговое окно, нажмите кнопку **заголовочный файл (.h)**.  
  
3.  В **имя** введите **annotations.h** и нажмите кнопку **добавить**.  
  
4.  Скопируйте следующий код и вставьте его в **annotations.h** файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактора.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  В обозревателе решений щелкните правой кнопкой мыши **исходные файлы**, пункты **New**, а затем нажмите кнопку **новый элемент**.  
  
6.  В **Добавление нового элемента** диалоговое окно, нажмите кнопку **кода** и нажмите кнопку **файл C++ (.cpp)**  
  
7.  В **имя** введите **annotations.cpp** и нажмите кнопку **добавить**.  
  
8.  Скопируйте следующий код и вставьте его в **annotations.cpp** файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактора.  
  
    ```cpp
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
  
9. Нажмите кнопку **файл** меню, а затем нажмите **сохранить все**.