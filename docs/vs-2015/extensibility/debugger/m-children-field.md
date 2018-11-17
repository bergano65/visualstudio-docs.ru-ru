---
title: Поля m_children | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f044c2dae278a0656f1f9e4c41a3940d87658a64
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731032"
---
# <a name="mchildren-field"></a>Поле m_children
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Список дочерних задач, которые зарегистрированы с помощью этой задачи.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Примечания  
 Пока выполняется задача, только потоку, который выполняет задачу должен получить доступ к этот массив.  
  
 Если задача завершена, другие потоки могут обращаться к этому полю, пока они не ничего добавлять к нему и не удаляйте ничего из него.  
  
## <a name="see-also"></a>См. также  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)

