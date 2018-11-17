---
title: IDebugProgramEx2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 829a6f009471a517687316252f0711b5ac7da89c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727214"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс позволяет сеанс отладки manager (SDM) присоединиться к программе и получить узел программы, связанный с программой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский порт поставщик реализует этот интерфейс на один и тот же объект как [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс, чтобы позволить SDM присоединиться к программе в том случае, когда в то же время позволяя поставщика порта для отслеживания всех сеансов подключен к программа. Если он выбирает поставщика пользовательского порта можно реализовать этот интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовы SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на `IDebugProgram2` интерфейс для получения этого интерфейса позволяет отслеживать сеансы, которые были присоединены к программам.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgramEx2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Присоединяет программу к сеансу.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Получает узел программы, связанный с программой.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс является закрытым между SDM и программой.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

