---
title: "Редактор и языковой службы расширения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 67d250a2806b367a76fa593026f10d4b671c21b2
ms.lasthandoff: 02/22/2017

---
# <a name="editor-and-language-service-extensions"></a>Редактор и расширения службы языка
Можно расширить большинство функций в редакторе кода Visual Studio. Редактор основана на Windows Presentation Foundation (WPF) и записана в управляемом коде. Хотя такой подход отличается от схемы в более ранних версиях Visual Studio, он предоставляет большинство тех же функций. Чтобы расширить редактор, следует используйте Managed Extensibility Framework (MEF).  
  
 Пакет SDK для Visual Studio предоставляет адаптеров, известный как *оболочки* для поддержки пакетов VSPackages, написанных для предыдущих версий. Тем не менее при наличии существующего VSPackage, рекомендуется обновить новую технологию, чтобы получить лучшую производительность и надежность.  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Общие сведения об использовании шаблонов элементов редактора.|  
|[Расширение редактора и языковые службы](../extensibility/extending-the-editor-and-language-services.md)|Ссылки на документы, описывающие проектирования и возможности редактора core показано, как расширить ее.|  
|[Устаревшие интерфейсы в редакторе](../extensibility/legacy-interfaces-in-the-editor.md)|Ссылки на документы, в которых объясняется, как получить доступ к базового редактора из существующего кода.|  
|[Создание пользовательские редакторы и конструкторы](../extensibility/creating-custom-editors-and-designers.md)|Ссылки на документы, в которых описаны способы создания пользовательских редакторов.|  
|[Расширяемость устаревших языковой службы](../extensibility/internals/legacy-language-service-extensibility.md)|Ссылки на документы, в которых описывается интеграция языков программирования в Visual Studio.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Представляет Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Введение в Windows Presentation Foundation (WPF).|
