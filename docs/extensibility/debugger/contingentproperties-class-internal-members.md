---
title: "Класс ContingentProperties - внутренние члены | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d5d929f41a40d986aafa8150e68fadcb46f3469
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="contingentproperties-class---internal-members"></a>Класс ContingentProperties - внутренние элементы
Содержит дополнительные свойства для <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
 Так как не удается получить доступ к эти внутренние члены из платформы .NET Framework, синтаксиса предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Члены  
  
### <a name="fields"></a>Поля  
  
|Имя|Описание|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Список дочерних задач, которые зарегистрированы с помощью этой задачи.|  
  
## <a name="remarks"></a>Примечания  
 Платформа .NET Framework инициализирует поля этого класса, только в том случае, если они требуются.  
  
## <a name="see-also"></a>См. также  
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)