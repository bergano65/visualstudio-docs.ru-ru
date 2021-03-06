---
title: Страница "Подписывание" в конструкторе проектов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5707ef277892c37cab16f78ac11113194a95e190
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663502"
---
# <a name="signing-page-project-designer"></a>Страница "Подписывание" в конструкторе проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Используйте страницу **Подписывание** **конструктора проектов** для подписи манифестов приложения и развертывания, а также сборок (подпись с помощью строгих имен).

 Обратите внимание, что подпись манифестов приложения и развертывания отличается от подписи сборки, хотя обе задачи выполняются на странице **Подписывание**.

 Кроме того, хранилище сведений о файле ключа для подписи манифеста и сборки различается. Для подписи манифеста сведения о ключе хранятся в базе данных криптографического хранилища на вашем компьютере и в хранилище сертификатов текущего пользователя Windows. Для подписи сборки информация о ключе хранится только в базе данных криптографического хранилища на вашем компьютере.

 Чтобы открыть страницу **Подписывание**, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. После того, как откроется окно **Конструктор проектов**, перейдите на вкладку **Подписывание**.

## <a name="application-and-deployment-manifest-signing"></a>Подписание манифестов приложения и развертывания
 **Подписать манифесты ClickOnce** установите этот флажок, чтобы подписать манифесты приложения и развертывания с помощью пары открытого и закрытого ключей. Дополнительные сведения о том, как это сделать, см. в разделе [Практическое руководство. Подписание манифестов приложения и развертывания](../../ide/how-to-sign-application-and-deployment-manifests.md).

 Кнопка **выбрать из хранилища** позволяет выбрать существующий сертификат из личного хранилища сертификатов текущего пользователя. Один из этих сертификатов можно выбрать, чтобы подписать манифесты приложения и развертывания.

 При нажатии кнопки **Выбрать из хранилища** открывается диалоговое окно **Выбор сертификата**, где перечислены сертификаты в вашем хранилище личных сертификатов, которые действительны в настоящее время (с неистекшим сроком действия) и имеют закрытые ключи. Назначение выбранного сертификата должно включать в себя подписывание кода.

 Если щелкнуть элемент **Просмотр свойств сертификатов**, открывается диалоговое окно **Сведения о сертификате**. Это диалоговое окно содержит подробные сведения о сертификате и дополнительные параметры. Можно щелкнуть элемент **Подробнее о сертификатах** для просмотра дополнительных справочных сведений.

 Кнопка **выбрать из файла** позволяет выбрать сертификат из существующего файла ключа.

 При нажатии кнопки **Выбрать из файла** открывается диалоговое окно **Выбор файла**, где можно выбрать файл ключа сертификата (PFX). Этот файл должен быть защищен паролем и пока отсутствовать в вашем хранилище личных сертификатов.

 В диалоговом окне **Введите пароль, чтобы открыть файл** введите пароль для открытия файла ключа сертификата (PFX). Сведения о пароле хранятся в списке контейнера личных ключей и хранилище личных сертификатов.

 Кнопка **создать тестовый сертификат** позволяет создать сертификат для тестирования. Тестовый сертификат используется для подписи манифестов развертывания и приложения ClickOnce.

 При выборе элемента **Создание тестового сертификата** открывается диалоговое окно **Создание тестового сертификата**, в котором можно ввести пароль для файла ключа строгого имени для тестового сертификата. Этот файл имеет имя *имя_проекта*_TemporaryKey.pfx. Если нажать кнопку **ОК** без ввода пароля, PFX-файл не шифруется с использованием пароля.

 Поле " **URL-адрес сервера меток времени** " указывает адрес сервера, на который подписана подпись. При предоставлении сертификата этот внешний сайт проверяет время подписывания приложения.

## <a name="assembly-signing"></a>Подпись сборки
 **Подписать сборку** флажок Установите этот флажок, чтобы подписать сборку и создать файл ключа со строгим именем. Дополнительные сведения о подписи сборки с помощью **конструктора проектов** см. в разделе [Практическое руководство. Подписывание сборки (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564).

 Этот параметр использует средство Al.exe, предоставляемое [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)], для подписи сборки. Дополнительные сведения о Al.exe см. в разделе [Практическое руководство. Подписание сборки строгим именем](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 **Выбор списка файлов ключей строгого имени** позволяет указать новый или существующий файл ключа с строгой подписью, используемый для подписи сборки. Выберите **\<Обзор...>** , чтобы выбрать существующий файл ключа.

 Выберите **\<Создать...>** , чтобы создать файл для подписи сборки. Открывается диалоговое окно **Создание ключа строгого имени**, в котором можно указать имя файла ключа и защитить этот файл паролем. Пароль должен содержать по меньшей мере 6 символов. Если пароль задан, создается файл обмена личной информацией (PFX); если пароль не указан, создается файл ключа со строгим именем (SNK).

 Кнопка " **изменить пароль** " изменяет пароль для файла ключа обмена личной информацией (PFX), который используется для подписания сборки.

 При выборе элемента **Смена пароля** открывается диалоговое окно **Изменение пароля ключа**. В поле **Старый пароль** этого диалогового окна указан текущий пароль для файла ключа. **Новый пароль** должен содержать по меньшей мере 6 символов. Информация о пароле хранится в хранилище сертификатов текущего пользователя Windows.

 Флажок **только отложенная подпись** установите этот флажок, чтобы включить отложенную подпись.

 В случае отложенной подписи проект нельзя выполнить или отладить. Однако можно использовать [Sn.exe (программа Strong Name)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) с параметром `-Vr`, чтобы пропустить проверку во время разработки.

> [!NOTE]
> При подписи сборки у вас не всегда может быть доступ к закрытому ключу. Например, организация может использовать тщательно охраняемую пару ключей, не предоставляемую разработчикам для повседневного использования. Открытый ключ может быть доступен, однако доступ к закрытому ключу может предоставляться лишь нескольким сотрудникам. В этом случае можно использовать *отложенную* или *частичную подпись* для предоставления открытого ключа, отложив добавление закрытого ключа до передачи сборки.

## <a name="see-also"></a>См. также раздел
 [Свойства проекта Справочник по](../../ide/reference/project-properties-reference.md) [управлению сборками и манифестом подпись](../../ide/managing-assembly-and-manifest-signing.md) [строгим именем подпись для управляемых приложений](https://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5) [руководство. Подписание манифестов приложения и развертывания](../../ide/how-to-sign-application-and-deployment-manifests.md) [руководство. Подписывание сборки (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564) [Пошаговое руководство. Подписание сборки](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) сборками со [строгими именами](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
