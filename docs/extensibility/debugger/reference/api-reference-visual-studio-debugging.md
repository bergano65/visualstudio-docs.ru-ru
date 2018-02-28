---
title: "Справочник по API (Visual Studio для отладки) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9f6e3110ca4988fcc12e547f3bcd82c1026f3aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="api-reference-visual-studio-debugging"></a>Справочник по API (отладки Visual Studio)
Этот раздел включает концептуальный обзор API, руководство, которое показывает их синтаксис и использование для всех элементов API и целый ряд примеров кода. Все ссылки, перечислены в алфавитном порядке по категориям.  
  
 В следующей таблице показаны распространенные `HRESULT` значения, возвращаемые методами.  
  
|name|Описание:|Значение|  
|----------|-----------------|-----------|  
|S_OK|Выполнено.|0x00000000|  
|E_UNEXPECTED|Непредвиденная ошибка.|0x8000FFFF|  
|E_NOTIMPL|Не реализовано.|0x80004001|  
|E_OUTOFMEMORY|Недостаточно памяти для завершения операции.|0x8007000E|  
|E_INVALIDARG|Один или несколько аргументов являются недопустимыми.|0x80070057|  
|E_NOINTERFACE|Интерфейс не поддерживается.|0x80004002|  
|E_POINTER|Недопустимый указатель.|отметкой 0x80004003|  
|E_HANDLE|Недопустимый дескриптор.|0x80070006|  
|E_ABORT|Операция прервана.|0x80004004|  
|E_FAIL|Непредвиденная ошибка.|0x80004005|  
|E_ACCESSDENIED|Ошибка доступа.|0x80070005|  
  
> [!NOTE]
>  Когда [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладки метод возвращает `S_OK`, предполагается, что все указатели параметра являются допустимыми, то есть проверка не проводится на out параметр указатели при `S_OK` возвращается.  
  
> [!NOTE]
>  Недопустимый или `NULL` [параметры out] может вызвать сбой интегрированной среде разработки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Вспомогательные функции пакета SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Расширяемость отладчика Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)