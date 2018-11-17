---
title: IEnumDebugCodeContexts2 | Документация Майкрософт
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
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 484ad1b1a084d40fe86c3ba36c90fdbc5cc4effa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773838"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс перечисляет контексты кода, связанного с сеанса отладки, или с определенной программой или документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка контекстов кода в определенном текстовом позиции в программе или список контекстов кода для контекста определенного документа.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) для получения этого интерфейса, представляющий список контекстов кода определенного текста в позиции программы исходного документа.  
  
 Вызовите [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) для получения этого интерфейса, представляющий список всех контекстов кода в конкретный документ-источник.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugCodeContexts2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Извлекает указанное число контекстов кода в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Пропускает заданное число контекстов кода в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Получает число контекстов кода в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio вызывает [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) для заполнения списка контекстов кода пользователь может выбрать из когда установка следующего оператора или отображение дизассемблированного кода для исходного файла. Несколько контекстов кода может произойти, например, при наличии нескольких экземпляров шаблона стиля C++.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)

