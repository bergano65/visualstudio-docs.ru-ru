---
title: "Элемент ASSEMBLY (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9032fa397e8fb4cb443d0209853ba4cfe7a5e53f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="assembly-element-visual-studio-templates"></a>Элемент Assembly (шаблоны Visual Studio)
Указывает сведения о сборке, используемые шаблоном для добавления в проекты ссылки на эту сборку.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Ссылки на >  
 \<Ссылка >  
 \<Сборки >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Ссылки](../extensibility/reference-element-visual-studio-templates.md)|Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Данный текст задает сборку, чтобы добавить в проект при создании экземпляра шаблона элемента. Имя сборки необходимо указать в одном из следующих способов:  
  
-   Как полное имя сборки. Например:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Как простая текстовая ссылка. Пример:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Примечания  
 `Assembly` — обязательный дочерний элемент элемента `Reference`.  
  
 `Reference`, `References,` И `Assembly` элементы могут использоваться только в VSTEMPLATE-файлах, имеющих `Type` значение атрибута `Item`.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется `TemplateContent` элемента шаблона элемента. Этот XML-код добавляет ссылки на сборки System.dll и System.Data.dll.  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)