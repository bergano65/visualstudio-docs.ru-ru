---
title: "Элемент Assembly (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly - элемент [шаблоны Visual Studio]"
  - "элемент <Assembly> [шаблоны Visual Studio]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Элемент Assembly (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает сведения о сборке, используемые шаблоном для добавления в проекты ссылки на эту сборку.  
  
## Синтаксис  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Ссылки](../extensibility/reference-element-visual-studio-templates.md)|Задает ссылку на сборку, которая добавляется при добавлении элемента в проект.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Данный текст указывает сборку, добавляемую к проекту при создании шаблона элемента.  Имя сборки должно быть задано одним из следующих способов.  
  
-   Как полное имя сборки.  Примеры.  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Как простая текстовая ссылка.  Примеры.  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## Заметки  
 `Assembly` является обязательным дочерним элементом элемента `Reference`.  
  
 Элементы `Reference`, `References,` и `Assembly` могут использоваться только в VSTEMPLATE\-файлах, атрибут `Type` которых имеет значение `Item`.  
  
## Пример  
 В следующем примере демонстрируется элемент `TemplateContent` шаблона элемента.  Этот XML добавляет ссылки на сборки System.dll и System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)