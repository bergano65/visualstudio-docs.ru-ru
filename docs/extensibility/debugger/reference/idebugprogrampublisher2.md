---
title: "IDebugProgramPublisher2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9251a24e1b52359a5c3f0810dced96cf69a3309b
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Этот интерфейс позволяет ядра отладки (DE) или пользовательский порт поставщиков для регистрации программы для отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для регистрации, чтобы сделать их видимыми для отладки в нескольких процессах отлаживаемых программ.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов COM `CoCreateInstance` работать с `CLSID_ProgramPublisher` для получения этого интерфейса (см. пример). DE или пользовательский порт поставщик использует этот интерфейс для регистрации программы узлы, представляющие отлаживаемых программ.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Предоставляет узел программы DEs и сеанса отладки manager (SDM).|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Удаляет узел программы, чтобы она больше недоступна.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Позволяет программе DEs и SDM.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Удаление программы, поэтому она больше недоступна.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Задает флаг, указывающий, что отладчик присутствует.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс доступны программы и программы узлов (то есть «публикует» их) для использования DEs и диспетчера сеанса отладки (SDM). Открыть опубликованные программы и программы узлов с помощью [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейса. Это единственный способ Visual Studio можно узнать, что программа отлаживается.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Пример  
 В этом примере показано, как создать экземпляр издателя программы и регистрации узла программы. Эти метаданные берутся из учебника [публикации узла программы](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae).  
  
```cpp#  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
