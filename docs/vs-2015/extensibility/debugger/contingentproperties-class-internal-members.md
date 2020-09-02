---
title: Класс Континжентпропертиес — внутренние элементы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f6778aef90361a7751ccd744fcf93822f8f97db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414650"
---
# <a name="contingentproperties-class---internal-members"></a>Внутренние элементы: класс ContingentProperties
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Содержит дополнительные свойства <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как вы не можете получить доступ к этим внутренним членам из .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Участники  
  
### <a name="fields"></a>Поля  
  
|Имя|Описание|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Список дочерних задач, зарегистрированных в этой задаче.|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework инициализирует поля этого класса только в том случае, если они необходимы.  
  
## <a name="see-also"></a>См. также:  
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
