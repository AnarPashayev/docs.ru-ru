---
title: Настраиваемое действие SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: d760f95b8e98bae52341296b90008e72d5c47d1f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637656"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="1e4b9-102">Настраиваемое действие SendMail</span><span class="sxs-lookup"><span data-stu-id="1e4b9-102">SendMail Custom Activity</span></span>
<span data-ttu-id="1e4b9-103">В образце описывается создание настраиваемого действия, которое является производным от <xref:System.Activities.AsyncCodeActivity>, для отправки почты с помощью SMTP для работы в приложении рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="1e4b9-104">Настраиваемое действие использует возможности <xref:System.Net.Mail.SmtpClient> асинхронно отправлять электронную почту и для отправки почты с проверкой подлинности.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="1e4b9-105">При этом также обеспечивается возможность использования таких возможностей конечных пользователей, как тестовый режим, замена маркеров, шаблоны файлов и тестовый путь размещения файла.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="1e4b9-106">В следующей таблице представлены аргументы для действия `SendMail`.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="1e4b9-107">name</span><span class="sxs-lookup"><span data-stu-id="1e4b9-107">Name</span></span>|<span data-ttu-id="1e4b9-108">Тип</span><span class="sxs-lookup"><span data-stu-id="1e4b9-108">Type</span></span>|<span data-ttu-id="1e4b9-109">Описание</span><span class="sxs-lookup"><span data-stu-id="1e4b9-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1e4b9-110">Узел</span><span class="sxs-lookup"><span data-stu-id="1e4b9-110">Host</span></span>|<span data-ttu-id="1e4b9-111">String</span><span class="sxs-lookup"><span data-stu-id="1e4b9-111">String</span></span>|<span data-ttu-id="1e4b9-112">Адрес узла SMTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="1e4b9-113">Порт</span><span class="sxs-lookup"><span data-stu-id="1e4b9-113">Port</span></span>|<span data-ttu-id="1e4b9-114">String</span><span class="sxs-lookup"><span data-stu-id="1e4b9-114">String</span></span>|<span data-ttu-id="1e4b9-115">Порт службы SMTP на узле.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="1e4b9-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="1e4b9-116">EnableSsl</span></span>|<span data-ttu-id="1e4b9-117">bool</span><span class="sxs-lookup"><span data-stu-id="1e4b9-117">bool</span></span>|<span data-ttu-id="1e4b9-118">Указывает, использует ли <xref:System.Net.Mail.SmtpClient> протокол SSL для шифрования соединения.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="1e4b9-119">UserName</span><span class="sxs-lookup"><span data-stu-id="1e4b9-119">UserName</span></span>|<span data-ttu-id="1e4b9-120">String</span><span class="sxs-lookup"><span data-stu-id="1e4b9-120">String</span></span>|<span data-ttu-id="1e4b9-121">Имя пользователя для настройки учетных данных для проверки подлинности свойства <xref:System.Net.Mail.SmtpClient.Credentials%2A> отправителя.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="1e4b9-122">Пароль</span><span class="sxs-lookup"><span data-stu-id="1e4b9-122">Password</span></span>|<span data-ttu-id="1e4b9-123">String</span><span class="sxs-lookup"><span data-stu-id="1e4b9-123">String</span></span>|<span data-ttu-id="1e4b9-124">Пароль для настройки учетных данных для проверки подлинности свойства <xref:System.Net.Mail.SmtpClient.Credentials%2A> отправителя.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="1e4b9-125">Субъект</span><span class="sxs-lookup"><span data-stu-id="1e4b9-125">Subject</span></span>|<span data-ttu-id="1e4b9-126"><xref:System.Activities.InArgument%601>\<строка ></span><span class="sxs-lookup"><span data-stu-id="1e4b9-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="1e4b9-127">Тема сообщения.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-127">Subject of the message.</span></span>|  
|<span data-ttu-id="1e4b9-128">Текст</span><span class="sxs-lookup"><span data-stu-id="1e4b9-128">Body</span></span>|<span data-ttu-id="1e4b9-129"><xref:System.Activities.InArgument%601>\<строка ></span><span class="sxs-lookup"><span data-stu-id="1e4b9-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="1e4b9-130">Текст сообщения.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-130">Body of the message.</span></span>|  
|<span data-ttu-id="1e4b9-131">Вложения</span><span class="sxs-lookup"><span data-stu-id="1e4b9-131">Attachments</span></span>|<span data-ttu-id="1e4b9-132"><xref:System.Activities.InArgument%601>\<строка ></span><span class="sxs-lookup"><span data-stu-id="1e4b9-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="1e4b9-133">Коллекцию вложений, используемую для хранения данных, вложенных в это сообщение электронной почты.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="1e4b9-134">Исходный тип</span><span class="sxs-lookup"><span data-stu-id="1e4b9-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="1e4b9-135">Адрес отправителя для данного сообщения электронной почты.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-135">From address for this email message.</span></span>|  
|<span data-ttu-id="1e4b9-136">Кому</span><span class="sxs-lookup"><span data-stu-id="1e4b9-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="1e4b9-137">Коллекцию адресов, содержащую получателей данного сообщения электронной почты.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="1e4b9-138">CC</span><span class="sxs-lookup"><span data-stu-id="1e4b9-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="1e4b9-139">Коллекция, содержащую получателей скрытой копии (CC) данного сообщения электронной почты адресов.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="1e4b9-140">BCC</span><span class="sxs-lookup"><span data-stu-id="1e4b9-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="1e4b9-141">Коллекцию адресов, содержащую получателей скрытой копии (BCC) данного сообщения электронной почты.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="1e4b9-142">лексемы</span><span class="sxs-lookup"><span data-stu-id="1e4b9-142">Tokens</span></span>|<span data-ttu-id="1e4b9-143"><xref:System.Activities.InArgument%601>< IDictionary\<строка, строка >></span><span class="sxs-lookup"><span data-stu-id="1e4b9-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="1e4b9-144">Маркеры для замены в тексте.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-144">Tokens to replace in the body.</span></span> <span data-ttu-id="1e4b9-145">Эта возможность позволяет пользователям указывать определенные значением в тексте сообщения, которые можно позднее заменить маркерами, предоставляемыми при использовании этого свойства.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="1e4b9-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="1e4b9-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="1e4b9-147">String</span><span class="sxs-lookup"><span data-stu-id="1e4b9-147">String</span></span>|<span data-ttu-id="1e4b9-148">Путь к шаблону текста.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-148">Path of a template for the body.</span></span> <span data-ttu-id="1e4b9-149">Действие `SendMail` копирует содержимое этого файла в свойство текста.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="1e4b9-150">Этот шаблон может содержать токены, которые заменяются на содержимое свойства Tokens.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="1e4b9-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="1e4b9-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="1e4b9-152">Если это свойство имеет значение, все сообщения электронной почты отправляются на адрес, указанный в нем.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="1e4b9-153">Это свойство планируется использовать при тестировании рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="1e4b9-154">Например если вы хотите убедиться, что все сообщения электронной почты отправляются без отправки их фактическое получателям.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="1e4b9-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="1e4b9-155">TestDropPath</span></span>|<span data-ttu-id="1e4b9-156">String</span><span class="sxs-lookup"><span data-stu-id="1e4b9-156">String</span></span>|<span data-ttu-id="1e4b9-157">Если это свойство имеет значение, все сообщения электронной почты, также сохраняются в указанном файле.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="1e4b9-158">Это свойство предназначено для использования при тестировании или отладке рабочих процессов, чтобы убедиться в том, что подходит формат и содержимое исходящие сообщения электронной почты.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="1e4b9-159">Содержимое решения</span><span class="sxs-lookup"><span data-stu-id="1e4b9-159">Solution Contents</span></span>  
 <span data-ttu-id="1e4b9-160">Решение содержит два проекта.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="1e4b9-161">Проект</span><span class="sxs-lookup"><span data-stu-id="1e4b9-161">Project</span></span>|<span data-ttu-id="1e4b9-162">Описание</span><span class="sxs-lookup"><span data-stu-id="1e4b9-162">Description</span></span>|<span data-ttu-id="1e4b9-163">Важные файлы</span><span class="sxs-lookup"><span data-stu-id="1e4b9-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="1e4b9-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="1e4b9-164">SendMail</span></span>|<span data-ttu-id="1e4b9-165">Действие SendMail</span><span class="sxs-lookup"><span data-stu-id="1e4b9-165">The SendMail activity</span></span>|<span data-ttu-id="1e4b9-166">1.  SendMail.cs: реализация для основных действий</span><span class="sxs-lookup"><span data-stu-id="1e4b9-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="1e4b9-167">2.  SendMailDesigner.xaml и SendMailDesigner.xaml.cs:конструктор для действия SendMail</span><span class="sxs-lookup"><span data-stu-id="1e4b9-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="1e4b9-168">3.  MailTemplateBody.htm: шаблон для исходящих сообщений электронной почты.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="1e4b9-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="1e4b9-169">SendMailTestClient</span></span>|<span data-ttu-id="1e4b9-170">Клиент для тестирования действий SendMail.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="1e4b9-171">В этом проекте описываются два способа вызова действия SendMail: декларативно и программно.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="1e4b9-172">1.  Sequence1.xaml: рабочий процесс, вызывающий действие SendMail.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="1e4b9-173">2.  Program.cs: вызывает Sequence1, а также программно создает рабочий процесс, который использует SendMail.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="1e4b9-174">Дополнительная настройка действия SendMail</span><span class="sxs-lookup"><span data-stu-id="1e4b9-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="1e4b9-175">Хотя она не показана в образце, пользователи могут выполнять дополнительную настройку действия SendMail.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="1e4b9-176">Эта дополнительная настройка описывается в следующих трех разделах.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="1e4b9-177">Отправка сообщения электронной почты с использованием маркеров, указанных в тексте сообщения</span><span class="sxs-lookup"><span data-stu-id="1e4b9-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="1e4b9-178">В этом фрагменте кода описывается отправка сообщения электронной почты с маркеров в тексте сообщения.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="1e4b9-179">Обратите внимание на то, как маркеры включены в текст сообщения.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="1e4b9-180">Значения для этих маркеров предоставлены для свойства маркеров.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="1e4b9-181">Отправка сообщения электронной почты с использованием шаблона</span><span class="sxs-lookup"><span data-stu-id="1e4b9-181">Sending an email using a template</span></span>  
 <span data-ttu-id="1e4b9-182">В этом фрагменте описывается отправка сообщения электронной почты с использованием маркеров шаблона в тексте.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="1e4b9-183">Обратите внимание, что при задании свойства `BodyTemplateFilePath` не нужно указывать значение для свойства Body (содержимое файла шаблона будет скопировано в текст).</span><span class="sxs-lookup"><span data-stu-id="1e4b9-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="1e4b9-184">Отправка сообщений в тестовом режиме</span><span class="sxs-lookup"><span data-stu-id="1e4b9-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="1e4b9-185">В этом фрагменте кода показано задание двух свойств тестирования:, задав `TestMailTo` на все сообщения будут отправляться `john.doe@contoso.con` (без учета значений, Cc, Bcc).</span><span class="sxs-lookup"><span data-stu-id="1e4b9-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="1e4b9-186">При задании TestDropPath все исходящие сообщения электронной почты будут также записываться по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="1e4b9-187">Эти свойства могут быть заданы независимо (они не связаны друг с другом).</span><span class="sxs-lookup"><span data-stu-id="1e4b9-187">These properties can be set independently (they are not related).</span></span>  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="1e4b9-188">Инструкции по установке</span><span class="sxs-lookup"><span data-stu-id="1e4b9-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="1e4b9-189">В этом образце необходим доступ к SMTP-серверу.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="1e4b9-190">Дополнительные сведения о настройке SMTP-сервера см. следующие ссылки.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- [<span data-ttu-id="1e4b9-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="1e4b9-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [<span data-ttu-id="1e4b9-192">Настройка службы SMTP (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="1e4b9-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [<span data-ttu-id="1e4b9-193">IIS 7.0: Настройка электронной почты SMTP</span><span class="sxs-lookup"><span data-stu-id="1e4b9-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [<span data-ttu-id="1e4b9-194">Установка службы SMTP</span><span class="sxs-lookup"><span data-stu-id="1e4b9-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="1e4b9-195">Эмуляторы SMTP разработки сторонних производителей можно загрузить из Интернета.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="1e4b9-196">Запуск образца</span><span class="sxs-lookup"><span data-stu-id="1e4b9-196">To run this sample</span></span>  
  
1. <span data-ttu-id="1e4b9-197">С помощью Visual Studio 2010, откройте решения SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-197">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="1e4b9-198">Убедитесь, что имеется доступ к работающему SMTP-серверу.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="1e4b9-199">См. инструкции по настройке.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-199">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="1e4b9-200">Настройте программу, задав адрес сервера, с и на адреса электронной почты.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="1e4b9-201">Чтобы правильно запустить этот пример, необходимо настроить значение и адреса электронной почты и адрес SMTP-сервера в файле Program.cs и sequence.XAML.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="1e4b9-202">Потребуется изменение адреса в обоих расположениях, поскольку программа отправляет сообщения двумя различными способами</span><span class="sxs-lookup"><span data-stu-id="1e4b9-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="1e4b9-203">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="1e4b9-204">Чтобы запустить решение, нажмите клавиши CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e4b9-205">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e4b9-206">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1e4b9-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e4b9-207">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e4b9-208">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1e4b9-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
