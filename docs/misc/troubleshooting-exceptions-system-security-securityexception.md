---
title: "Разрешение вопросов, связанных с исключениями: System.Security.SecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "System.Security.SecurityException - класс"
  - "SecurityException - класс"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Security.SecurityException
Исключение <xref:System.Security.SecurityException> возникает при обнаружении ошибки безопасности.  
  
## Полезные советы  
 Настройте уровень разрешения сборки с помощью страницы свойств.  
 Для получения дополнительной информации см. <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>.  
  
 Храните данные приложения в изолированном хранилище.  
 Изолированное хранилище — это хранилище данных, обеспечивающее автономность и безопасность, путем определения стандартизованных способов сопоставления кода с защищенными данными. Дополнительные сведения см. в разделе [Изолированное хранилище](../Topic/Isolated%20Storage.md).  
  
 Если используется <xref:System.Windows.Forms.OpenFileDialog>, используйте метод <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> для открытия или сохранения файла.  
 Это позволяет приложению выполняться в ситуации частичного доверия.  
  
 Убедитесь, что приложение читает и пишет в существующие журналы событий на локальном компьютере.  
 Приложение может не иметь необходимых разрешений для создания журналов на локальном компьютере или записи на него.  
  
 Если вызываете неуправляемые библиотеки, используйте эквивалентные управляемые библиотеки.  
 В .NET Framework может существовать эквивалентный API. Для получения дополнительной информации см. [Устранение неполадок взаимодействия](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability).  
  
 Используйте безопасные окна.  
 Перечисление <xref:System.Security.Permissions.UIPermissionWindow> указывает тип доступа к окну, допустимому для использования вызывающим кодом.  
  
 Разрешите пользователям печатать посредством компонента <xref:System.Windows.Forms.PrintDialog>.  
 Это позволяет приложению выполняться в ситуации частичного доверия. Для получения дополнительной информации см. <xref:System.Windows.Forms.PrintDialog>.  
  
 Печатайте на принтер по умолчанию.  
 Это позволяет приложению выполняться в ситуации частичного доверия. Может быть попытка доступа к принтеру, на который нет прав.  
  
 Получайте данные с того же веб\-сервера, с которого было развернуто.  
 Это позволяет приложению выполняться в ситуации частичного доверия.  
  
 При развертывании решения Microsoft Office проверьте, что выполнены все необходимые требования безопасности.  
 Дополнительные сведения см. в разделе [Рекомендации по обеспечению безопасности для решений Office](/office-dev/office-dev/specific-security-considerations-for-office-solutions).  
  
 Если сборка, реализующая особый объект системы безопасности, ссылается на другие сборки, добавьте их в список полностью доверенных сборок.  
 Для получения дополнительной информации см. [Caspol.exe \(Code Access Security Policy Tool\)](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md).  
  
## См. также  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)