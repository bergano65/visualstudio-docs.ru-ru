---
title: "Обеспечение безопасности решений Office | Документы Microsoft"
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
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
ms.assetid: af840916-dda4-4e52-b536-802ebcab30ca
caps.latest.revision: "78"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 45052deff58e992b427f72188fcb0dc8ade91b95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="securing-office-solutions"></a>Обеспечение безопасности решений Office
  Модель безопасности для решений Office использует несколько технологий: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], Центр управления безопасностью в Microsoft Office и зону ограниченных узлов браузера Internet Explorer. Работа различных возможностей безопасности описана в следующих разделах.  
  
-   [Присвоение уровня доверия решениям Office](#GrantingTrustToSolutions)  
  
-   [Присвоение уровня доверия документам](#GrantingTrustToDocuments)  
  
-   [Предоставление доверия при использовании установщика Windows](#GrantingTrustWindowsInstaller)  
  
-   [Рекомендации по обеспечению безопасности для решений Office](#Security)  
  
-   [Безопасность во время разработки](#SecurityDuringDeployment)  
  
-   [Visual Studio Tools для Office Runtime](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a>Присвоение уровня доверия решениям Office  
 Присвоение уровня доверия решениям Office означает изменение политики безопасности для каждого конечного пользователя таким образом, что доверие решению Office предоставляется на основании следующего свидетельства.  
  
-   Сертификат, используемый для подписания манифеста развертывания.  
  
-   URL-адрес манифеста развертывания.  
  
 Дополнительные сведения см. в разделе [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a>Присвоение уровня доверия документам  
 Настройка уровня документа требует, чтобы документ находился в каталоге, назначенном в качестве надежного расположения. Для получения дополнительной информации см. [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a>Предоставление доверия при использовании установщика Windows  
 Чтобы создать MSI-файл для установки решений Office в каталог Program Files, можно использовать установщик Windows. Для этого требуются права администратора. Для решений Office в каталог Program Files средств Visual Studio 2010 для среды выполнения Office считает эти решения Office доверенными и не выводит запрос о доверии ClickOnce.  
  
##  <a name="Security"></a>Рекомендации по обеспечению безопасности для решений Office  
 Средства безопасности, предоставляемые [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] и Microsoft Office, помогают защитить решения Office от различных угроз безопасности. Дополнительные сведения см. в разделе [Specific Security Considerations for Office Solutions](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a>Безопасность во время разработки  
 Чтобы упростить процесс разработки, Visual Studio задает политику безопасности, требуемую для выполнения и отладки решения на компьютере, при каждой сборке проекта. В некоторых случаях могут потребоваться дополнительные меры обеспечения безопасности при разработке проекта.  
  
### <a name="document-level-solutions"></a>Решения уровня документа  
 При разработке следующих типов проектов необходимо добавить полный путь к документу в список надежных расположений в приложении Microsoft Office.  
  
-   Решения, которые на общем сетевом ресурсе, например на уровне документа  *\\\servername\sharename*.  
  
-   Решения уровня документа для Word, использующие файлы с расширениями DOC и DOCM.  
  
 При добавлении местоположения документа в список надежных расположений включите подкаталоги или конкретно укажите папки для отладки и сборки. Дополнительные сведения см. в статье справки Microsoft Office Online [создание, удаление или изменение надежного расположения для файлов](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Временные сертификаты  
 Если сертификат для подписи еще не существует, Visual Studio создает временный сертификат. Этот временный сертификат следует использовать только во время разработки, а для развертывания необходимо приобрести официальный сертификат.  
  
 Временный сертификат создается после первой сборки проекта Office. При последующем нажатии клавиши F5 сборка проекта выполняется заново, поскольку проект помечается как измененный при добавлении сертификата.  
  
 Через некоторое время может накопиться большое количество временных сертификатов, поэтому их нужно периодически удалять.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a>Visual Studio Tools для Office Runtime  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Содержит функции для проверки удостоверения издателя и разрешений, выданных для настройки. Он проверяет разрешения, выполняя последовательность проверок безопасности.  
  
### <a name="security-during-customization-loading"></a>Безопасность во время загрузки настройки  
 Во время загрузки настройки уровня документа, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] всегда проверяет, является ли документ в список надежных расположений. Кроме того среда выполнения проверяет, требует ли решение FullTrust в манифесте приложения. Во время загрузки настройки он не выполняет дополнительные проверки безопасности.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Последовательность проверок безопасности во время установки  
 При установке или обновлении решения Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] выполняет ряд проверок безопасности в определенной последовательности для принятия решения о доверии. Решение устанавливается или обновляется только в том случае, если среда выполнения определяет, что это решение является доверенным.  
  
 Процесс установки можно запустить одним из четырех способов: с помощью программы установки, открыв манифест развертывания, открыв узел приложения Microsoft Office или запустив файл VSTOInstaller.exe.  
  
 Первая проверка безопасности применяется только к решениям уровня документа. Документ, принадлежащий решению уровня документа, должен находиться в надежном расположении. Если документ находится в удаленной сетевой общей папке либо имеет расширение имени файла DOC или DOCM, расположение документа необходимо добавить в список надежных расположений. Для получения дополнительной информации см. [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
 ![Безопасность VSTO – Установка с Microsoft Office](../vsto/media/host-install.png "Безопасность VSTO – Установка с Microsoft Office")  
  
 Следующий набор проверок безопасности выполняется [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и ClickOnce. Чтобы пройти эти проверки, решений Office должны запрашивать разрешения FullTrust, быть подписаны сертификатом, который отсутствует в списке недоверенных издателей и находиться в расположении, не находится в зоне ограниченных узлов обозревателя Internet Explorer. Если сертификат находится в списке надежных издателей, решение устанавливается немедленно. В противном случае, если решение проходит все проверки, оно передается на последний этап проверок.  
  
 ![Безопасность VSTO для установки решений](../vsto/media/installing.png "Безопасность VSTO для установки решений")  
  
 Если [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] разрешен запрос о доверии и решение еще не был предоставлен доверия, среда выполнения позволяет сделать конечным пользователем решение о доверии. Если пользователь предоставляет решению доверие, в пользовательский список включения добавляется запись. Все решения в пользовательском списке включения имеют полное доверие и могут быть установлены и запущены.  
  
 Начиная с версии Visual Studio 2010, список включения игнорируется в том случае, если решение Office установлено с помощью установщика Windows (MSI) в каталог Program Files. Дополнительные сведения см. в разделе [предоставление доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![Безопасность VSTO – с помощью программы установки для установки](../vsto/media/setup-vstoinstaller.png "Безопасность VSTO – с помощью программы установки для установки")  
  
## <a name="see-also"></a>См. также  
 [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)   
 [Присвоение уровня доверия документам](../vsto/granting-trust-to-documents.md)   
 [Предоставление доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Как: настройка безопасности списка включения](../vsto/how-to-configure-inclusion-list-security.md)   
 [Как: подписывание решений Office](../vsto/how-to-sign-office-solutions.md)   
 [Устранение неполадок безопасности решений Office](../vsto/troubleshooting-office-solution-security.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Справочник по ClickOnce](/visualstudio/deployment/clickonce-reference)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  