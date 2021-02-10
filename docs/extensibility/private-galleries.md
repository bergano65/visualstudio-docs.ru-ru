---
title: Частные галереи | Документация Майкрософт
description: Узнайте, как предоставить общий доступ к элементам управления, шаблонам и средствам, разрабатываемым в пакете SDK для Visual Studio, отправляя их в частную галерею.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5b58c5885f4fc9bd3765c818ea414bee0dbf3c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961863"
---
# <a name="private-galleries"></a>Частные коллекции
Вы можете совместно использовать элементы управления, шаблоны и средства, которые вы разрабатываете, отправляя их в *частную коллекцию* в интрасети организации следующим образом:

- Создайте канал Atom (RSS) в соответствующим образом настроенном центральном расположении (репозитории) в интрасети. Дополнительные сведения см. [в разделе инструкции. Создание веб-канала Atom для частной коллекции](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Распространите *pkgdef* -файл, описывающий частную коллекцию. Рекомендуется использовать эту конфигурацию для администраторов, желающих одновременно подключать частную коллекцию к нескольким компьютерам.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Добавление частной коллекции в расширения и обновления в Visual Studio
 Если доступна частная коллекция, ее можно добавить в **расширения и обновления** в Visual Studio.

 ![Диалоговое окно "Добавить" диспетчера расширений](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Добавление частной коллекции к расширениям и обновлениям

1. В строке меню выберите **Сервис** > **Параметры**.

2. В узле **Среда** выберите **расширения и обновления**.

3. Выберите кнопку **Добавить**.

4. В поле **имя** введите имя для частной коллекции, например `My Gallery` .

5. В поле **URL-адрес** введите URL-адрес веб-канала Atom или сайта SharePoint, на котором размещается частная коллекция.

    1. Если узел является каналом Atom, который подключается к частной коллекции, URL-адрес будет выглядеть следующим образом: `http://www.mywebsite/mygallery/atom.xml` .  Этот URL-адрес может ссылаться на файл или сетевой путь.

    2. Если узел является сайтом SharePoint, URL-адрес будет выглядеть следующим образом: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Управление частными галереями
 Администратор может сделать закрытую галерею доступной для нескольких компьютеров одновременно, изменив системный реестр на каждом компьютере. Для этого создайте файл *pkgdef* , описывающий новые разделы реестра и их значения.  Этот файл имеет следующий формат.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Дополнительные сведения см. [в разделе руководство. Управление частной коллекцией с помощью параметров реестра](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Установка расширений из частной коллекции
 Вы можете искать и устанавливать расширения Visual Studio из частной коллекции в оснастке " **расширения и обновления**". В следующих шагах используется частная коллекция с именем `My Gallery` .

 ![Диспетчер расширений устанавливает закрытую галерею](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Поиск и Установка расширений из частной коллекции

1. В строке меню выберите **Сервис**  >  **расширения и обновления**.

2. В левой области выберите расширения в **Интернете**, а затем щелкните **Моя коллекция**.

3. В области справа выберите расширение, а затем нажмите кнопку **скачать** .

## <a name="update-extensions-from-a-private-gallery"></a>Обновление расширений из частной коллекции
 После публикации новых версий расширений Visual Studio в частной коллекции можно обновить установленные расширения. В следующих шагах используется частная коллекция с именем `My Repository` .

 ![Обновление закрытой галереи диспетчера расширений](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Обновление установленного расширения из частной коллекции

1. В строке меню выберите **Сервис**  >  **расширения и обновления**.

2. В левой области выберите **обновления**, а затем щелкните **Мой репозиторий**.

3. В области справа выберите расширение, а затем нажмите кнопку **Обновить** .

## <a name="see-also"></a>См. также раздел
- [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Поставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
