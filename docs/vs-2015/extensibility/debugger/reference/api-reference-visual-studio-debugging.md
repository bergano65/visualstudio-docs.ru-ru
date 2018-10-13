---
title: Справочник по API (Отладка Visual Studio) | Документация Майкрософт
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
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 979a6b999e34b5cec57e4a0d324f8c273fbe5dc2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222104"
---
# <a name="api-reference-visual-studio-debugging"></a>Справочник API (отладка Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

В справочном разделе включает в себя общие сведения об API, направляющей, демонстрирует синтаксис и использование для всех элементов API, а также целый ряд примеров кода. Все ссылки перечислены в алфавитном порядке по категориям.  
  
 В следующей таблице приведены распространенные `HRESULT` значения, возвращаемые методами.  
  
|name|Описание|Значение|  
|----------|-----------------|-----------|  
|S_OK|Выполнено.|0x00000000|  
|E_UNEXPECTED|Непредвиденная ошибка.|0x8000FFFF|  
|E_NOTIMPL|Не реализовано.|0x80004001|  
|E_OUTOFMEMORY|Недостаточно памяти для завершения операции.|0x8007000E|  
|E_INVALIDARG|Один или несколько аргументов являются недопустимыми.|0x80070057|  
|E_NOINTERFACE|Интерфейс не поддерживается.|0x80004002|  
|E_POINTER|Недопустимый указатель.|0x80004003|  
|E_HANDLE|Недопустимый дескриптор.|0x80070006|  
|E_ABORT|Операция прервана.|0x80004004|  
|E_FAIL|Непредвиденная ошибка.|0x80004005|  
|E_ACCESSDENIED|Ошибка доступа.|0x80070005|  
  
> [!NOTE]
>  Когда [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] отладки метод возвращает `S_OK`, предполагается, что все указатели параметра являются допустимыми, то есть проверка не проводится на out параметр указателей при `S_OK` возвращается.  
  
> [!NOTE]
>  Недопустимый или `NULL` [параметров out] может привести к сбою в работе интегрированной среды разработки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Расширяемость отладчика Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

