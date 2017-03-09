---
title: "Регистрация служб | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "службы, регистрация"
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Регистрация служб
Для поддержки загрузки по запросу поставщик служб должен зарегистрировать глобальные службы в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Во время разработки поставщики управляемых служб регистрируют службы и переопределения служб путем добавления атрибутов в исходный код для пакетов, а затем выполняют сборку пакетов в IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Это запускает служебную программу RegPkg.exe в результирующей сборке, регистрируя пакет и подготавливая его к развертыванию. Для получения дополнительной информации см. [Практическое руководство. Регистрация службы](../misc/how-to-register-a-service.md).  
  
 Поставщики неуправляемых служб должны регистрировать предоставляемые службы в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], в разделе "Службы" или "Переопределения служб" системного реестра. В следующем фрагменте REG\-файла показано, как служба SVsTextManager может быть зарегистрирована:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
```  
  
 В примере выше номер версии — версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например, 7.1 или 8.0, ключ {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} является идентификатором службы \(SID\), SVsTextManager, а значение по умолчанию {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} является GUID пакета диспетчера текстов VSPackage, который предоставляет службу.  
  
## Удаленные службы и фоновые потоки  
 Службы, которые вы предоставляете, не предоставляются автоматически удаленно или в фоновые потоки. Чтобы сделать их доступными, вам нужно выполнить сборку и зарегистрировать библиотеку типов.  
  
 Из неуправляемого кода, который использует библиотеку Visual Studio \(VSL\), вы можете зарегистрировать свою библиотеку типов следующим образом:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE #include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Из управляемого кода вы можете добавить действие после сборки следующим образом:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## См. также  
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основы службы](../extensibility/internals/service-essentials.md)