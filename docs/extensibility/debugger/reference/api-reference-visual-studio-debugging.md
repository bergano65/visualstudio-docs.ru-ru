---
title: "Справочник по API (отладки Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], справочник по API"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Справочник по API (отладки Visual Studio)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Концептуальный обзор раздел включает ссылки API, направляющих в которой приведен синтаксис и потребление для всех элементов api\-интерфейса, а также ряд примеров кода.  Все ссылки, перечислены в алфавитном порядке по категориям.  
  
 Следующая таблица показывает общее `HRESULT` значения, возвращаемые методами.  
  
|Имя|Описание|Значение|  
|---------|--------------|--------------|  
|S\_OK|Успех.|0x00000000|  
|E\_UNEXPECTED|Непредвиденный сбой.|0x8000FFFF|  
|E\_NOTIMPL|Не реализован.|0x80004001|  
|E\_OUTOFMEMORY|Недостаточно памяти для выполнения операции.|0x8007000E|  
|E\_INVALIDARG|Один или более аргументов являются недопустимыми.|0x80070057|  
|E\_NOINTERFACE|Нет такого поддерживаемого интерфейса.|0x80004002|  
|E\_POINTER|Недопустимый указатель.|0x80004003|  
|E\_HANDLE|Недопустимый дескриптор.|0x80070006|  
|E\_ABORT|Прерватьая операции.|0x80004004|  
|E\_FAIL|Непредвиденный сбой.|0x80004005|  
|E\_ACCESSDENIED|Без ограничений к было отказано ошибка.|0x80070005|  
  
> [!NOTE]
>  При a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] метод отладки возвращает  `S_OK`предполагается, что все указатели параметра out является допустимым, то есть проверка не дирижирована в указателях параметра, если out  `S_OK` возвращает.  
  
> [!NOTE]
>  Недопустимо или `NULL` \[out\] параметры могут вызвать сбой интегрированной среды разработки.  
  
## См. также  
 [Интерфейсы](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Расширение возможностей отладчика Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)