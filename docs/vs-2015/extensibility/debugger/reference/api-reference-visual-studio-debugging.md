---
title: Справочник по API (Отладка Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e95200cf29c8561798c858635c3864d635fb40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842593"
---
# <a name="api-reference-visual-studio-debugging"></a>Справочник API (отладка Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Справочный раздел содержит концептуальный обзор API, руководство, в котором показан синтаксис и использование для всех элементов API, а также ассортимент примеров кода. Все ссылки перечислены в алфавитном порядке по категориям.  
  
 В следующей таблице показаны общие `HRESULT` значения, возвращаемые методами.  
  
|Имя|Описание|Значение|  
|----------|-----------------|-----------|  
|S_OK|Успешно.|0x00000000|  
|E_UNEXPECTED|Непредвиденный сбой.|0x8000FFFF|  
|E_NOTIMPL|Не реализовано.|0x80004001|  
|E_OUTOFMEMORY|Недостаточно памяти для завершения операции.|0x8007000E|  
|E_INVALIDARG|Один или несколько аргументов недопустимы.|0x80070057|  
|E_NOINTERFACE|Такой интерфейс не поддерживается.|0x80004002|  
|E_POINTER|Недопустимый указатель.|0x80004003|  
|E_HANDLE|Недопустимый маркер.|0x80070006|  
|E_ABORT|Операция аварийно завершена.|0x80004004|  
|E_FAIL|Непредвиденный сбой.|0x80004005|  
|E_ACCESSDENIED|Общая ошибка отказа в доступе.|0x80070005|  
  
> [!NOTE]
> При [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] возврате из метода отладки `S_OK` предполагается, что все указатели на параметры являются допустимыми, т `S_OK` . е. при возвращении указателей на параметры не выполняется проверка.  
  
> [!NOTE]
> Недопустимые или `NULL` [исходящие] параметры могут привести к сбою интегрированной среды разработки.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейс](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Вспомогательные методы SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Расширяемость отладчика Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
