---
title: Xamarin Forms (MVVM) Dependency Services
category: Xamarin
tags: [xamarin, code]
---

Generate random string

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
private static Random random = new Random();

public static string RandomString(int length)
{
    const string chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
    return new string(Enumerable.Repeat(chars, length)
      .Select(s => s[random.Next(s.Length)]).ToArray());
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Validate Email

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public static bool IsValidEmail(string emailaddress)
{
    try
    {
        MailAddress m = new MailAddress(emailaddress);
        return true;
    }
    catch (System.FormatException)
    {
        return false;
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Image Source to Byte Array

Code
----

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ c#
public static byte[] ImageSourceToByteArray(ImageSource source)
{
    StreamImageSource streamImageSource = (StreamImageSource)source;
    System.Threading.CancellationToken cancellationToken = System.Threading.CancellationToken.None;
    Task<Stream> task = streamImageSource.Stream(cancellationToken);
    Stream stream = task.Result;

    byte[] b;
    using (MemoryStream ms = new MemoryStream())
    {
        stream.CopyTo(ms);
        b = ms.ToArray();
    }

    return b;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

