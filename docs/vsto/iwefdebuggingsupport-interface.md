---
title: "Интерфейс IWefDebuggingSupport | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Интерфейс IWefDebuggingSupport
  Реализованный средой отладки, такие как Visual Studio, чтобы упростить отладку приложений для office.  Приложение office, например слово или Excel, получает этот интерфейс из Visual Studio и затем вызывает методы интерфейса на некоторые шаги во время сеанса отладки.  
  
## Синтаксис  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## Методы  
 В следующей таблице перечислены методы, IWefDebuggingSupport определяет интерфейс.  
  
|Имя|Описание|  
|---------|--------------|  
|[Метод GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Возвращает сведения о приложениях для office, автоматически вставляются во время отладки.|  
|[Метод SetWefProcessId](../vsto/setwefprocessid-method.md)|Предоставляет идентификатор процесса, выполняемого содержимое .NET Framework расширений Интернета \(WEF\).|  
  
  