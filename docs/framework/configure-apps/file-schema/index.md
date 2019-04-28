---
title: Схема файлов конфигурации для .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: 6ebb6487136bff567c57143e3000a20270c1f87e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705289"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>Схема файлов конфигурации для .NET Framework

Файлы конфигурации — это стандартные XML-файлы, которые можно использовать для изменения параметров и установки политик для приложений. Схема конфигурации .NET Framework состоит из элементов, которые можно использовать в файлах конфигурации для управления поведением приложений. Оглавление данного раздела отражает иерархию схемы для запуска, среды выполнения, сети и других типов параметров конфигурации.

Сведения о типах, формате и расположении файлов конфигурации см. в статье [Настройка приложений](~/docs/framework/configure-apps/index.md). Для редактирования файлов конфигурации напрямую необходимо иметь представление о языке XML.

> [!IMPORTANT]
> В тегах и атрибутах XML в файлах конфигурации учитывается регистр.

## <a name="in-this-section"></a>Содержание раздела

[Элемент **\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md). Описание элемента `<configuration>`, который является элементом верхнего уровня для всех файлов конфигурации.

[Элемент **\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Определяет политику привязки сборок на уровне конфигурации.

[Элемент **\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md). Задает файл конфигурации, который следует включить.

[Схема параметров запуска](~/docs/framework/configure-apps/file-schema/startup/index.md). Описание элементов, определяющих версию среды CLR, которая будет использоваться.

[Схема параметров среды выполнения](~/docs/framework/configure-apps/file-schema/runtime/index.md). Описание элементов настройки привязки сборок и поведения во время выполнения.

[Схема параметров сети](~/docs/framework/configure-apps/file-schema/network/index.md). Описание элементов, указывающих способ подключения платформы .NET Framework к Интернету.

[Схема параметров шифрования](~/docs/framework/configure-apps/file-schema/cryptography/index.md). Описание элементов, с помощью которых можно сопоставить понятные имена алгоритмов с классами, реализующими алгоритмы шифрования.

[Схема разделов конфигурации](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md). Описание элементов, используемых для создания и применения разделов конфигурации с пользовательскими параметрами.

[Схема параметров трассировки и отладки](~/docs/framework/configure-apps/file-schema/trace-debug/index.md). Описание элементов, определяющих переключатели и прослушиватели трассировки.

[Схема параметров поставщиков языков и компиляторов](~/docs/framework/configure-apps/file-schema/compiler/index.md). Параметры поставщиков языков и компиляторов определяют элементы конфигурации компиляторов для доступных поставщиков языков.

[Схема прикладных параметров](~/docs/framework/configure-apps/file-schema/application-settings-schema.md). Описание элементов, позволяющих приложению Windows Forms или ASP.NET сохранять и извлекать параметры области определения приложения и параметры области пользователя.

[Схема параметров приложения](~/docs/framework/configure-apps/file-schema/appsettings/index.md). Содержит пользовательские параметры приложения, такие как пути к файлам, URL-адреса XML-веб-служб и другие сведения о пользовательской конфигурации приложения.

[Схема веб-параметров](~/docs/framework/configure-apps/file-schema/web/index.md). Все элементы схемы веб-параметров, в том числе элементы настройки способов работы ASP.NET с ведущими приложениями, такими как службы IIS. Используются в файлах *Aspnet.config*.

[Схема конфигурации Windows Forms](winforms/index.md). Все элементы в разделе конфигурации приложения Windows Forms, который включает в себя такие настройки, как поддержка нескольких мониторов и высокого DPI.

[Схема конфигурации WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md). Все элементы, которые позволяют настроить службу WCF и клиентские приложения.

[Синтаксис директивы WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md). Описание директивы `@ServiceHost`, которая определяет относящиеся к странице атрибуты, используемые компилятором SVC.

[Схема конфигурации WIF](windows-identity-foundation/index.md). Все элементы схемы конфигурации Windows Identity Foundation (WIF).

## <a name="related-sections"></a>Связанные разделы

[Схема параметров удаленного взаимодействия](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)). Описание элементов, настраивающих клиентские и серверные приложения, реализующие удаленное взаимодействие.

[Схема параметров ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)). Описание элементов, управляющих поведением веб-приложений ASP.NET.

[Схема параметров веб-служб](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)). Описание элементов, которые управляют поведением веб-служб ASP.NET и их клиентов.

[Настройка приложений .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)). Описание способов настройки безопасности, привязки сборок и удаленного взаимодействия в платформе .NET Framework.
