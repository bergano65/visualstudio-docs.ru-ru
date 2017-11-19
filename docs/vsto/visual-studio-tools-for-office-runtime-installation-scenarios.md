---
title: "Visual Studio Tools for Office сценарии установки среды выполнения | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Visual Studio Tools for Office runtime, installation scenarios
ms.assetid: 71f34daf-8163-4a53-a401-9cab6581f30d
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e09d83fefee766ce19c71812bccfa751cc90e27e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools for Office Runtime Installation Scenarios
  Установку среды выполнения набора средств Visual Studio 2010 для Office можно выполнять на трех разных этапах:  
  
-   Во время установки Visual Studio.  
  
-   Во время установки Microsoft Office.  
  
-   Во время установки распространяемого пакета среды выполнения набора средств Visual Studio 2010 для Office.  
  
 Установленные компоненты среды выполнения зависят от конфигурации компьютера и сценария установки.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Компоненты среды выполнения, устанавливаемые в каждом сценарии установки  
 Среда выполнения набора средств Visual Studio 2010 для Office содержит три компонента: загрузчик решений Office, расширения Office для платформы .NET Framework 3.5 и расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии. Загрузчик решений Office всегда устанавливается при установке среды выполнения. Установка расширений Office для платформы .NET Framework зависит от конфигурации компьютера и сценария установки. Если одно из расширений Office невозможно установить при установке среды выполнения, среда автоматически установит отсутствующие расширения Office позже при соблюдении определенных требований. Этот компонент среды выполнения называется *установить по запросу*.  
  
 В следующей таблице указывается, какие компоненты среды выполнения устанавливаются по умолчанию в каждом сценарии установки среды выполнения. Дополнительные сведения о каждом сценарии представлены далее.  
  
|Сценарий установки среды выполнения|Загрузчик решений Office|Расширения Office для платформы .NET Framework 3.5|Расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Расширения Office для [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|С [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] и более поздними версиями|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Да|Да|  
|С [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Нет|Нет|  
|С Office 2010 с пакетом обновления 1 (SP1) или более поздней версии|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Да, если платформа [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] уже установлена.|Нет|  
|С распространяемой средой выполнения|Да|Да, если платформа .NET Framework 3.5 уже установлена.|Да, если платформа [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] уже установлена.|Да, если платформа [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] уже установлена.|  
  
### <a name="installing-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Установка среды выполнения с Visual Studio или Microsoft Office Developer Tools для Visual Studio  
 При установке Office Developer Tools в Visual Studio расширения Office для [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] и [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] всегда устанавливаются на компьютере разработчика. Расширения Office для платформы .NET Framework 3.5 устанавливаются только в том случае, если .NET Framework 3.5 уже имеется на компьютере разработчика. Если вы устанавливаете платформу .NET Framework 3.5 после установки [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], среда выполнения автоматически установит расширения Office для .NET Framework 3.5 при первом создании проекта Office, ориентированном на .NET Framework 3.5.  
  
> [!WARNING]  
>  Создать проект Office, ориентированный на платформу .NET Framework 3.5, с помощью [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] или более поздней версии, нельзя.  
  
 Дополнительные сведения об установке Office developer tools см. в разделе [как: Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="installing-the-runtime-with-office"></a>Установка среды выполнения с Office  
 При установке Office расширения Office для платформы .NET Framework 3.5 устанавливаются в случае, если .NET Framework 3.5 уже имеется на компьютере. При установке платформы .NET Framework 3.5 после Office среда выполнения автоматически установит расширения Office для .NET Framework 3.5, когда приложение Office попытается в первый раз загрузить решение, ориентированное на .NET Framework 3.5.  
  
 Расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии не устанавливаются с Office даже в том случае, если [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздняя версия уже имеется на момент установки Office.  
  
 Расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] устанавливаются вместе с Office. Конечные пользователи могут получить расширения Office для [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] путем установки обновления Windows.  
  
 Чтобы гарантировать, что пользователи будут иметь необходимые расширения для применения вашего приложения, включите распространяемый пакет последней версии среды выполнения набора средств Visual Studio 2010 для Office в качестве необходимого компонента для своего решения. Дополнительные сведения о необходимых компонентах см. в разделе [необходимые компоненты для развертывания решения Office](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="installing-the-runtime-by-using-the-runtime-redistributable"></a>Установка среды выполнения с помощью распространяемого пакета среды выполнения  
 Для установки среды выполнения можно вручную запустить распространяемый пакет среды выполнения набора средств Visual Studio 2010 для Office или включить этот пакет в качестве необходимого компонента при развертывании решения Office.  
  
 При установке среды выполнения с помощью распространяемого пакета среды выполнения набора средств Visual Studio 2010 для Office расширения Office для платформы .NET Framework 3.5 и расширения Office для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии будут установлены, если соответствующие версии платформы .NET Framework уже имеются на компьютере. Если при установке среды выполнения одна из этих версий платформы .NET Framework на компьютере отсутствует, расширения Office для отсутствующей версии платформы .NET Framework не будут установлены. Если вы установите отсутствующую версию платформы .NET Framework позже, среда выполнения автоматически установит соответствующие расширения Office, когда решение, для которого требуются эти расширения, будет в следующий раз установлено (если среда выполнения была установлена с решением, развернутым с помощью ClickOnce) или загружено (если среда выполнения была установлена с решением, развернутым с помощью установщика Windows).  
  
 Дополнительные сведения о включении в решение ClickOnce необходимых компонентов см. в разделе [как: Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Дополнительные сведения об установке среды выполнения из распространяемого пакета вручную см. в разделе [как: Установка набора средств Visual Studio для распространяемого пакета среды выполнения Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Сборки инструментов Visual Studio для среды выполнения Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  