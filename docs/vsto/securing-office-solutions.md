---
title: Безопасные решения Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fb5f5577fc1c8e51ddac8b51b64cae1891dfbee6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820842"
---
# <a name="secure-office-solutions"></a>Безопасные решения Office
  Модель безопасности для решений Office включает несколько технологий: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], Центр управления безопасностью в Microsoft Office и зону ограниченных узлов браузера Internet Explorer. Работа различных возможностей безопасности описана в следующих разделах.

- [Предоставление доверия решениям Office](#GrantingTrustToSolutions)

- [Предоставить доверие к документам](#GrantingTrustToDocuments)

- [Предоставление доверия при использовании установщика Windows](#GrantingTrustWindowsInstaller)

- [Рекомендации по обеспечению безопасности для решений Office](#Security)

- [Безопасность во время разработки](#SecurityDuringDeployment)

- [Visual Studio Tools для Office runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="GrantingTrustToSolutions"></a> Предоставление доверия решениям Office
 Присвоение уровня доверия решениям Office означает изменение политики безопасности для каждого конечного пользователя таким образом, что доверие решению Office предоставляется на основании следующего свидетельства.

- Сертификат, используемый для подписания манифеста развертывания.

- URL-адрес манифеста развертывания.

  Дополнительные сведения см. в разделе [предоставления доверия решениям Office](../vsto/granting-trust-to-office-solutions.md).

##  <a name="GrantingTrustToDocuments"></a> Предоставить доверие к документам
 Настройка уровня документа требует, чтобы документ находился в каталоге, назначенном в качестве надежного расположения. Дополнительные сведения см. в разделе [предоставления доверия к документам](../vsto/granting-trust-to-documents.md).

##  <a name="GrantingTrustWindowsInstaller"></a> Предоставление доверия при использовании установщика Windows
 Чтобы создать MSI-файл для установки решений Office в каталог Program Files, можно использовать установщик Windows. Для этого требуются права администратора. Для решений Office в каталог Program Files Visual Studio 2010 Tools для Office runtime считает эти решения Office доверенными и не выводит запрос о доверии ClickOnce.

##  <a name="Security"></a> Рекомендации по обеспечению безопасности для решений Office
 Средства безопасности, предоставляемые [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] и Microsoft Office, помогают защитить решения Office от различных угроз безопасности. Дополнительные сведения см. в разделе [рекомендации по обеспечению безопасности для решений Office](../vsto/specific-security-considerations-for-office-solutions.md).

##  <a name="SecurityDuringDeployment"></a> Безопасность во время разработки
 Чтобы упростить процесс разработки, Visual Studio задает политику безопасности, требуемую для выполнения и отладки решения на компьютере, при каждой сборке проекта. В некоторых случаях могут потребоваться дополнительные меры обеспечения безопасности при разработке проекта.

### <a name="document-level-solutions"></a>Решения уровня документа
 При разработке следующих типов проектов необходимо добавить полный путь к документу в список надежных расположений в приложении Microsoft Office.

- Решения, которые находятся в общей сетевой папки, такие как на уровне документа  *\\\servername\sharename*.

- Решения уровня документа для Word, использующие *.doc* или *.docm* файлов.

  При добавлении местоположения документа в список надежных расположений включите подкаталоги или конкретно укажите папки для отладки и сборки. Дополнительные сведения см. в статье справки Microsoft Office Online [создание, удаление или изменение надежного расположения для файлов](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Временные сертификаты
 Если сертификат для подписи еще не существует, Visual Studio создает временный сертификат. Этот временный сертификат следует использовать только во время разработки, а для развертывания необходимо приобрести официальный сертификат.

 Временный сертификат создается после первой сборки проекта Office. При последующем нажатии клавиши **F5**, проект будет перестроен, поскольку проект помечается как измененный при добавлении сертификата.

 Через некоторое время может накопиться большое количество временных сертификатов, поэтому их нужно периодически удалять.

##  <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools для Office runtime
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Содержит функции для проверки удостоверения издателя и разрешения, предоставленные для настройки. Он проверяет разрешения, выполняя последовательность проверок безопасности.

### <a name="security-during-customization-loading"></a>Безопасность во время загрузки настройки
 При загрузке настройки уровня документа, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] всегда проверяет, является ли документ в список надежных расположений. Кроме того среда выполнения проверяет, требует ли решение FullTrust в манифесте приложения. Во время загрузки настройки он не выполняет дополнительные проверки безопасности.

### <a name="sequence-of-security-checks-during-installation"></a>Последовательность проверок безопасности во время установки
 При установке или обновлении решения Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] выполняет ряд проверок безопасности в определенной последовательности для принятия решения о доверии. Решение устанавливается или обновляется только в том случае, если среда выполнения определяет, что это решение является доверенным.

 Процесс установки можно запустить одним из четырех способов: запустив программу установки, путем открытия манифеста развертывания, открыв узел приложения Microsoft Office или запустив *VSTOInstaller.exe*.

 Первая проверка безопасности применяется только к решениям уровня документа. Документ, принадлежащий решению уровня документа, должен находиться в надежном расположении. Если документ находится в удаленной сетевой общей папке или имеет *.doc* или *.docm* расширение имени файла в список надежных расположений необходимо добавить расположение документа. Дополнительные сведения см. в разделе [предоставления доверия к документам](../vsto/granting-trust-to-documents.md).

 ![Безопасность VSTO – Установка с Microsoft Office](../vsto/media/host-install.png "Безопасность VSTO – Установка с Microsoft Office")

 Следующий набор проверок безопасности выполняется [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] и ClickOnce. Чтобы пройти эти проверки, решения Office должны запрашивать разрешения FullTrust, быть подписан сертификатом, которого нет в списке недоверенных издателей и быть в расположении, которое не входит в зону ограниченных Internet Explorer. Если сертификат находится в списке надежных издателей, решение устанавливается немедленно. В противном случае, если решение проходит все проверки, оно передается на последний этап проверок.

 ![Безопасность VSTO для установки решений](../vsto/media/installing.png "Безопасность VSTO для установки решений")

 Если [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] разрешен запрос о доверии и решение еще не было предоставлено доверие, среда выполнения позволяет конечному пользователю принять решение о доверии. Если пользователь предоставляет решению доверие, в пользовательский список включения добавляется запись. Все решения в пользовательском списке включения имеют полное доверие и могут быть установлены и запущены.

 Начиная с версии Visual Studio 2010, список включения игнорируется в том случае, если решение Office установлено с помощью установщика Windows (MSI) в каталог Program Files. Дополнительные сведения см. в разделе [доверия Office решения с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Безопасность VSTO – с помощью программы установки для установки](../vsto/media/setup-vstoinstaller.png "Безопасность VSTO – с помощью программы установки для установки")

## <a name="see-also"></a>См. также

- [Предоставление доверия решениям Office](../vsto/granting-trust-to-office-solutions.md)
- [Предоставить доверие к документам](../vsto/granting-trust-to-documents.md)
- [Доверия решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Практическое руководство. Настройка безопасности списка включения](../vsto/how-to-configure-inclusion-list-security.md)
- [Практическое руководство. Подписывание решений Office](../vsto/how-to-sign-office-solutions.md)
- [Устранение неполадок с безопасностью решений Office](../vsto/troubleshooting-office-solution-security.md)
- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Справочные сведения ClickOnce](../deployment/clickonce-reference.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)
