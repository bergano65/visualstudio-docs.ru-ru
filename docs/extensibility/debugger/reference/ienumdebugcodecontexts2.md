---
title: IEnumDebugCodeContexts2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc6ff9a173bcfbb87606fe493697857d7ec2b323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122565"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Этот интерфейс перечисляет кода контекстов, связанные с сеансом отладки или с определенной программой или документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка контекстов кода для конкретного текста позиции в программе или список контекстов кода для контекста определенного документа.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) получить этот интерфейс, представляющий список контекстов кода для должности определенный текст в исходном документе программы.  
  
 Вызовите [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) получить этот интерфейс, представляющий список всех контекстов кода в конкретном исходном документе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugCodeContexts2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Извлекает указанное число контекстов код в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Пропускает указанное число контекстов код в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Возвращает число контекстов кода в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio вызывает [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) для заполнения списка контекстов кода пользователь может выбирать при установка следующего оператора или отображения дизассемблированного кода для исходного файла. Несколько контекстов код может произойти, например, при наличии нескольких экземпляров шаблона стиля C++.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)