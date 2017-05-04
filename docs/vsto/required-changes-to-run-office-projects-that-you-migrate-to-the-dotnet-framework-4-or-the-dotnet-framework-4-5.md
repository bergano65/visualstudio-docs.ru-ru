---
title: "Изменения, необходимые для выполнения проектов Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5 | Microsoft Docs"
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
helpviewer_keywords: 
  - "Office - проекты [разработка решений Office в Visual Studio], переход на платформу .NET Framework 4"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Изменения, необходимые для выполнения проектов Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5
  Если требуемая версия платформы .NET Framework проекта Office изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию с более ранней версии платформы .NET Framework, то, чтобы убедиться, что решение может выполняться на компьютере разработки и на компьютерах конечных пользователей, необходимо выполнить следующие задачи.  
  
-   Удалите <xref:System.Security.SecurityTransparentAttribute> из проекта, если он был обновлен с версии Visual Studio 2008.  
  
-   Выполните команду **Clean** в Visual Studio, чтобы иметь возможность выполнения или отладки проекта на компьютере разработчика.  
  
-   Обновите платформу .NET Framework, необходимую для проекта.  
  
-   Конечные пользователи также должны переустановить решение, если оно было развернуто с помощью технологии ClickOnce до того, как вы изменили целевую платформу.  
  
 Дополнительные сведения о всех этих задачах см. в соответствующих разделах ниже.  
  
## Удаление атрибута SecurityTransparent из проектов, которые обновляются с версии Visual Studio 2008  
 При обновлении проекта Office с версии Visual Studio 2008 и последующем изменении целевой платформы .NET Framework проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию атрибут <xref:System.Security.SecurityTransparentAttribute> необходимо удалить из проекта. Visual Studio не удаляет этот атрибут автоматически. Если не удалить этот атрибут, при компиляции проекта вы получите сообщение об ошибке.  
  
 Дополнительные сведения об условиях, в которых Visual Studio может изменить целевую платформу обновленного проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], см. в разделе [Обновление и перенос решений Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### Удаление атрибута SecurityTransparentAttribute  
  
1.  Откройте проект в Visual Studio, а затем откройте **Обозреватель решений**.  
  
2.  В узле **Свойства** \(для C\#\) или **Мой проект** \(для Visual Basic\) дважды щелкните файл кода AssemblyInfo, чтобы открыть его в редакторе кода.  
  
    > [!NOTE]  
    >  В проектах Visual Basic для просмотра файла с кодом AssemblyInfo необходимо нажать кнопку **Показать все файлы** в **обозревателе решений**.  
  
3.  Найдите <xref:System.Security.SecurityTransparentAttribute> и удалите его из файла или закомментируйте его.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## Выполнение команды очистки для отладки или запуска проекта на компьютере разработчика  
 Если проект Office был создан до изменения целевой платформы проекта на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, выполните команду **Очистить**, а затем перестройте проект после изменения целевой платформы.  Если не выполнить команду **Очистить**, при попытке отладки или запуска нового проекта вы получите <xref:System.Runtime.InteropServices.COMException>.  
  
 Дополнительные сведения о команде **Очистить** см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).  
  
## Обновление необходимых компонентов для развертывания  
 При переориентации проекта Office на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию необходимо также обновить соответствующие необходимые компоненты платформы .NET Framework в диалоговом окне **Необходимые компоненты**.  В противном случае процесс развертывания с помощью ClickOnce или проект InstallShield Limited Edition проверяет наличие предыдущей версии платформы .NET Framework и устанавливает ее.  
  
 Дополнительные сведения об обновлении компонентов, необходимых для развертывания на компьютерах конечных пользователей, см. в статье [Практическое руководство. Установка компонентов, необходимых для выполнения решений Office, на компьютерах конечных пользователей](http://msdn.microsoft.com/ru-ru/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## Повторная установка решений на компьютерах конечных пользователей  
 Если вы используете технологию ClickOnce для развертывания решения Office, которое ориентируется на платформу .NET Framework 3.5, а затем переориентируете проект на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо удалить решение, а затем переустановить после его повторной публикации.  Если вы повторно публикуете переориентированное решение и оно обновляется на компьютерах конечных пользователей, то эти пользователи получат <xref:System.Runtime.InteropServices.COMException> во время выполнения обновленного решения.  
  
## См. также  
 [Перенос решений Office на платформу .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  