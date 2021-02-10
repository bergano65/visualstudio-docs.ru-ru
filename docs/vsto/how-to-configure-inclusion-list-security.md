---
title: Как настроить безопасность списка включений
description: Настройте запрос о доверии ClickOnce, чтобы контролировать, предоставлены ли конечным пользователям возможность установки решений Office путем сохранения решения о доверии в списке включения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ddbc74c00c1e1f74ce078586d624e2da4dbd8163
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954024"
---
# <a name="how-to-configure-inclusion-list-security"></a>Как настроить безопасность списка включений
  При наличии разрешений администратора можно настроить [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] запрос о доверии, чтобы указать, будут ли конечные пользователи иметь возможность установки решений Office путем сохранения решения о доверии в списке включения. Дополнительные сведения о списках включения см. в разделе [Trusted Office Solutions with using Lists](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Для решений, которые находятся в каждой из пяти зон, можно задать следующие параметры.

- Включите [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] ключ запроса доверия и список включения. Можно разрешить конечным пользователям предоставлять доверие решениям Office, подписанным с помощью любого сертификата.

- Ограничьте [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] ключ запроса доверия и список включения. Можно разрешить конечным пользователям устанавливать решения Office, подписанные с помощью сертификата, который идентифицирует издателя, но не является доверенным.

- Отключите [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] ключ запроса доверия и список включения. Можно запретить конечным пользователям устанавливать любое решение Office, не подписанное явно доверенным сертификатом.

## <a name="enable-the-inclusion-list"></a>Включение списка включений
 Включите список включения для зоны, если нужно, чтобы конечные пользователи преддавали возможность установки и запуска любого решения Office, поступающих из этой зоны.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Включение списка включений с помощью редактора реестра

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.

    2. В поле **Открыть** введите **regedt32.exe** и нажмите кнопку **ОК**.

2. Найдите следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если раздел не существует, создайте его.

3. Добавьте следующие подразделы в качестве **строкового значения**, если они еще не существуют, со связанными значениями.

    |Подключ строкового значения|Значение|
    |-------------------------|-----------|
    |**Интернет**;|**аусентикодерекуиред**|
    |**унтрустедситес**|**Отключено**|
    |**Мой**|**Enabled**|
    |**Разрешений**|**Enabled**|
    |**трустедситес**|**Enabled**|

     По умолчанию в **Интернете** используется значение **Аусентикодерекуиред** , а **унтрустедситес** — значение **Disabled (отключено**).

### <a name="to-enable-the-inclusion-list-programmatically"></a>Включение списка включения программными средствами

1. Создайте Visual Basic или консольное приложение Visual C#.

2. Откройте файл *Program. vb* или *Program.CS* для редактирования и добавьте следующий код.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Создайте и запустите приложение.

## <a name="restrict-the-inclusion-list"></a>Ограничение списка включений
 Ограничьте список включения, чтобы решения были подписаны сертификатами Authenticode с известными удостоверениями, прежде чем пользователи получат запрос на принятие решения о доверии.

### <a name="to-restrict-the-inclusion-list"></a>Ограничение списка включений

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.

    2. В поле **Открыть** введите **regedt32.exe** и нажмите кнопку **ОК**.

2. Найдите следующий раздел реестра:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Если раздел не существует, создайте его.

3. Добавьте следующие подразделы в качестве **строкового значения**, если они еще не существуют, со связанными значениями.

    |Подключ строкового значения|Значение|
    |-------------------------|-----------|
    |**унтрустедситес**|**Отключено**|
    |**Интернет**;|**аусентикодерекуиред**|
    |**Мой**|**аусентикодерекуиред**|
    |**Разрешений**|**аусентикодерекуиред**|
    |**трустедситес**|**аусентикодерекуиред**|

     По умолчанию в **Интернете** используется значение **Аусентикодерекуиред** , а **унтрустедситес** — значение **Disabled (отключено**).

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Ограничение списка включения программными средствами

1. Создайте Visual Basic или консольное приложение Visual C#.

2. Откройте файл *Program. vb* или *Program.CS* для редактирования и добавьте следующий код.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Создайте и запустите приложение.

## <a name="disable-the-inclusion-list"></a>Отключение списка включений
 Список включения можно отключить, чтобы конечные пользователи могли устанавливать только те решения, которые подписаны надежным и известным сертификатом.

### <a name="to-disable-the-inclusion-list"></a>Отключение списка включений

1. Откройте редактор реестра:

    1. Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.

    2. В поле **Открыть** введите **regedt32.exe** и нажмите кнопку **ОК**.

2. Создайте следующий раздел реестра, если он еще не существует:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. Добавьте следующие подразделы в качестве **строкового значения**, если они еще не существуют, со связанными значениями.

    |Подключ строкового значения|Значение|
    |-------------------------|-----------|
    |**унтрустедситес**|**Отключено**|
    |**Интернет**;|**Отключено**|
    |**Мой**|**Отключено**|
    |**Разрешений**|**Отключено**|
    |**трустедситес**|**Отключено**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Отключение списка включений программным способом

1. Создайте Visual Basic или консольное приложение Visual C#.

2. Откройте файл *Program. vb* или *Program.CS* для редактирования и добавьте следующий код.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Выполните сборку и запустите приложение.

## <a name="see-also"></a>См. также раздел
- [Доверять решениям Office с помощью списков включения](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
