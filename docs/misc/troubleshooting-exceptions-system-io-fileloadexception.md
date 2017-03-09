---
title: "Разрешение вопросов, связанных с исключениями: System.IO.FileLoadException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FileLoadException - класс"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IO.FileLoadException
Исключение <xref:System.IO.FileLoadException> вызывается в случае, когда управляемая сборка найдена, но не может быть загружена.  
  
## Полезные советы  
 **Убедитесь, что этот файл является действительной сборкой .Net Framework.**  
 Это исключение вызывается, если файл не является допустимой сборкой .NET Framework. Для получения дополнительной информации см. <xref:System.Reflection.Assembly>.  
  
 **Проверьте, что сборка или модуль не был загружен дважды с двумя разными свидетельствами.**  
 Свидетельство — это набор сведений, используемых для принятия решений политики безопасности, например, сведений о разрешениях, которые могут быть предоставлены коду. Дополнительные сведения см. в разделах <xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A> и <xref:System.Reflection.Assembly.Evidence%2A>.  
  
 **Если используются методы RegisterAssembly или UnregisterAssembly, убедитесь, что длина имени сборки не превышает значение MAX\_PATH.**  
 Длина имени элемента сборки не может превышать MAX\_PATH. Дополнительные сведения см. в разделах <xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A> и <xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A>.  
  
 **Если загружается вспомогательная сборка, убедитесь, что её CultureInfo соответствует CultureInfo файла.**  
 Вспомогательные сборки содержат локализованные ресурсы, содержащие не локализуемый исполняемый код и ресурсы для одного языка и региональных параметров, которые используются по умолчанию или при нейтральном языке и региональных параметрах. Для получения дополнительной информации см. <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>.  
  
## См. также  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)