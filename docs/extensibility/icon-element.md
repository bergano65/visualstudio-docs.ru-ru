---
title: "Значок элемента | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, значок"
  - "Элемент Icon (VSCT XML-схемы)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Значок элемента
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Атрибут guid значок тега — это guid, определенный точечного рисунка.  Атрибут id выбирает слота в полосе точечного рисунка. Этот элемент является необязательным.  Если этот элемент отсутствует значение **guidOfficeIcon:msotcidNoIcon** будет неявно.  
  
## Синтаксис  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Идентификатор GUID|Обязательный. Идентификатор guid определенного точечного рисунка.|  
|id|Обязательный. Выбор области в полосе точечного рисунка.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Отсутствует.|Отсутствует.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент кнопки](../extensibility/buttons-element.md)||  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)