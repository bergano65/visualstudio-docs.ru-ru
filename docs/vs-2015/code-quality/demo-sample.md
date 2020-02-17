---
title: Демонстрационный пример | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 3a49859a8cd1c4ffb01f93bf2539fc16c42f8c4c
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277883"
---
# <a name="demo-sample"></a>Пример Demo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В следующих процедурах показано, как создать пример для [пошагового руководства: анализC++ кода C/Code для дефектов](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Эти процедуры создают следующее:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] решение с именем Кппдемо.  
  
- Проект статической библиотеки CodeDefects.  
  
- Проект статической библиотеки Annotations.  
  
  Процедуры также предоставляют код для заголовков и CPP для статических библиотек.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Создание решения CppDemo и проекта CodeDefects  
  
1. В меню **Файл** выберите команду **Создать**, а затем **Создать проект**.  
  
2. Если Visual C++ не является вашим языком по умолчанию в Visual Studio, в списке дерева **Типы проектов** разверните узел **Другие языки**.  
  
3. Разверните **Visual C++** и выберите **Общие**.  
  
4. В области **Шаблоны** щелкните **Пустой проект**.  
  
5. В текстовом поле **Имя** введите **CodeDefects**.  
  
6. Установите флажок **Создать каталог для решения**.  
  
7. В текстовом поле **Имя решения** введите **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Настройка проекта CodeDefects в качестве статической библиотеки  
  
1. В обозревателе решений щелкните правой кнопкой мыши проект **CodeDefects** и выберите пункт **Свойства**.  
  
2. Разверните пункт **Свойства конфигурации** и выберите **Общие**.  
  
3. В списке **Общие** выберите текст в столбце рядом с полем **Конечное расширение**, а затем введите **.lib**.  
  
4. В области **Значения по умолчанию для проекта** щелкните столбец рядом с полем **Тип конфигурации**, а затем выберите **Статическая библиотека (.lib)** .  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Добавление заголовка и исходного файла в проект CodeDefects  
  
1. В обозревателе решений разверните **CodeDefects**, щелкните правой кнопкой мыши элемент **Файлы заголовков**, выберите пункт **Добавить**, а затем пункт **Новый элемент**.  
  
2. В диалоговом окне **Добавление нового элемента** щелкните **Код** и выберите **Файл заголовка (.h)** .  
  
3. В поле **Имя** введите **Bug.cpp** и нажмите кнопку **Добавить**.  
  
4. Скопируйте приведенный ниже код и вставьте его в файл **Bug. cpp** в редакторе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
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
  
5. В обозревателе решений щелкните правой кнопкой мыши **Исходные файлы** и последовательно выберите пункты **Создать** и **Новый элемент**.  
  
6. В окне **Добавление нового элемента** щелкните **Файл C++ (.cpp)** .  
  
7. В поле **Имя** введите **Bug.cpp** и нажмите кнопку **Добавить**.  
  
8. Скопируйте приведенный ниже код и вставьте его в файл Bug. h в редакторе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
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
  
9. Откройте меню **Файл** и щелкните пункт **Сохранить все**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Добавление проекта Annotations и его настройка в качестве статической библиотеки  
  
1. В обозревателе решений щелкните **CppDemo** и последовательно выберите пункты **Добавить** и **Новый проект**.  
  
2. В диалоговом окне **Добавить новый проект** разверните узел Visual C++, выберите пункт **Общие** и пункт **Пустой проект**.  
  
3. В текстовом поле **Имя** введите **Annotations** и нажмите кнопку **Добавить**.  
  
4. В обозревателе решений щелкните правой кнопкой мыши проект **Annotations** и выберите пункт **Свойства**.  
  
5. Разверните пункт **Свойства конфигурации** и выберите **Общие**.  
  
6. В списке **Общие** выберите текст в столбце рядом с полем **Конечное расширение**, а затем введите **.lib**.  
  
7. В области **Значения по умолчанию для проекта** щелкните столбец рядом с полем **Тип конфигурации**, а затем выберите **Статическая библиотека (.lib)** .  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Добавление файла заголовка и исходного файла в проект Annotations  
  
1. В обозревателе решений разверните **Annotations**, щелкните правой кнопкой мыши элемент **Файлы заголовков**, выберите пункт **Добавить**, а затем пункт **Новый элемент**.  
  
2. В окне **Добавление нового элемента** щелкните **Файл заголовка (.h)** .  
  
3. В поле **Имя** введите **annotations.h** и нажмите кнопку **Добавить**.  
  
4. Скопируйте приведенный ниже код и вставьте его в файл **Annotations. h** в редакторе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
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
  
5. В обозревателе решений щелкните правой кнопкой мыши **Исходные файлы** и последовательно выберите пункты **Создать** и **Новый элемент**.  
  
6. В диалоговом окне **Добавление нового элемента** щелкните **Код** и выберите **Файл C++ (.cpp)** .  
  
7. В поле **Имя** введите **annotations.cpp** и нажмите кнопку **Добавить**.  
  
8. Скопируйте приведенный ниже код и вставьте его в файл **Annotations. cpp** в редакторе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
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
  
9. Откройте меню **Файл** и щелкните пункт **Сохранить все**.
