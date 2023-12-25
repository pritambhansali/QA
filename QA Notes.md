
`
package web.wisdomizer.main;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.testng.Assert;

import web.wisdomizer.factory.DriverFactory;

public class HelloWorld {

	public static void main(String[] args) throws Exception {

		/* ****** GET DRIVER ****** */
		WebDriver chromeDriver = DriverFactory.getChromeDriver();
		/* ****** LOAD THE PAGE ****** */
		chromeDriver.get("https://rahulshettyacademy.com/locatorspractice/");
//		System.out.println(chromeDriver.getTitle());
//		System.out.println(chromeDriver.getCurrentUrl());
//		https://rahulshettyacademy.com/locatorspractice/

		/* ****** IMPLICIT WAIT ****** */
		chromeDriver.manage().timeouts().implicitlyWait(Duration.ofSeconds(5));

		/* ****** ID SELECTOR ****** */
		chromeDriver.findElement(By.id("inputUsername")).sendKeys("Wisdomizer");

		/* ****** NAME SELECTOR ****** */
		chromeDriver.findElement(By.name("inputPassword")).sendKeys("Wisdomizer");

		/* ****** CSS SELECTOR ****** */
//		chromeDriver.findElement(By.cssSelector("button.submit")).click();

		/* ****** CSS SELECTOR REGULAR EXPRESSION ****** */
//		chromeDriver.findElement(By.cssSelector("button[type*='sub']")).click();

		/* ****** XPATH REGULAR EXPRESSION ****** */
		chromeDriver.findElement(By.xpath("//button[contains(@type,'sub')]")).click();

		System.out.println(chromeDriver.findElement(By.cssSelector("p.error")).getText());

		/* ****** LINK TEXT SELECTOR ****** */
		chromeDriver.findElement(By.linkText("Forgot your password?")).click();

		/* ****** XPATH SELECTOR ****** */
		chromeDriver.findElement(By.xpath("//input[@placeholder='Name']")).sendKeys("abc");
//		chromeDriver.findElement(By.xpath("//input[@placeholder='Email']")).sendKeys("def");
//		chromeDriver.findElement(By.xpath("//input[@placeholder='Phone Number']")).sendKeys("123");

		/* ****** XPATH SELECTOR FOR SIBLING NODE ****** */
		chromeDriver.findElement(By.xpath("//input[@type='text'][2]")).sendKeys("def");
//		chromeDriver.findElement(By.cssSelector("input[type='text']:nth-child(4)")).sendKeys("123");

		/* ****** CSS SELECTOR FOR SIBILING NODE ****** */
		chromeDriver.findElement(By.cssSelector("input[type='text']:nth-child(3)")).clear();

		/* ****** XPATH SELECTOR FOR CHILD NODE ****** */
		/* ****** Parent tag name / Child tag name ****** */
		chromeDriver.findElement(By.xpath("//form/input[3]")).sendKeys("12345");

		/* ****** CSS SELECTOR WITHOUT CLASS NAME ****** */
		/* ****** .tagname ****** */
		chromeDriver.findElement(By.cssSelector(".reset-pwd-btn")).click();

		/* ****** CSS SELECTOR FOR CHILD NODE ****** */
		/* ****** Parent Tag Name <SPACE> Child Tag Name ****** */
		System.out.println(chromeDriver.findElement(By.cssSelector("form p")).getText());

		chromeDriver.findElement(By.cssSelector(".go-to-login-btn")).click();

		chromeDriver.findElement(By.id("inputUsername")).sendKeys("rahul");
		chromeDriver.findElement(By.cssSelector("input[placeholder='Password']")).sendKeys("rahulshettyacademy");
		
		/*
		 * In case we need to find for all the elements which are having the attribute -> 
		 * placeholder = 'Password' then we can write it as below :
		 * chromeDriver.findElement(By.cssSelector("*[placeholder='Password']"));  
		 */

		Thread.sleep(1000);
		/* ****** CUSTOMISED XPATH SELECTOR USING CLASSNAME ****** */
		/* ****** SESSION 39 ****** */

//		WebDriverWait webDriverWait = new WebDriverWait(chromeDriver, Duration.ofSeconds(5));
//		webDriverWait.until(ExpectedConditions.elementToBeClickable(By.xpath("//button[@class='submit signInBtn']"))).click();
		chromeDriver.findElement(By.xpath("//button[@class='submit signInBtn']")).click();
		Thread.sleep(1000);
		System.out.println(chromeDriver.findElement(By.tagName("p")).getText());
		
		/*
		 * In case we need to refer to the text of an element instead of an attribute using XPATH then -
		 * for ex- <button class ='logout-btn' xpath='1'>Log Out</button>
		 * 
		 * //button[text()='Log Out'] or //*[text()='Log Out'] -> for all elements containing the text = Log Out
		 * 
		 */

		Assert.assertEquals(chromeDriver.findElement(By.tagName("p")).getText(), "You are successfully logged in.");

		chromeDriver.quit();
		
		/* Session 46
		 * Absolute Path - Starts from the root node. For this we can use single front slash - / 
		 * for ex - /html/body/header/
		 * 
		 * Relative Path - Starts from the tags any where in the dom structure apart from root tag.
		 * For this we can use double front slash.
		 * for ex - //header/p etc.
		 * 
		 * Traverse Siblings:-
		 * //header/div/button[1]/following-sibling::[1 or 2 or 3]
		 * //header/div/button[1]/parent::div/button[2 or 3]
		 * 
		 */
		
		
		

	}
}

`
---

`
package web.wisdomizer.main;

import org.openqa.selenium.WebDriver;

import web.wisdomizer.factory.DriverFactory;

public class BrowserNavigation {

	public static void main(String[] args) throws Exception {

		/*
		 * new
		 * URL("magnet:?xt=urn:btih:ab4a7f102224c9e7d99e8c9f8a2f59f80325a68a&dn=www.5MovieRulz.top - Salaar Cease Fire – Part 1 (2023) 720p Hindi DVDScr x264 AAC 1.6GB.mkv&tr=udp%3A%2F%2Ftracker.openbittorrent.com%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.torrent.eu.org%3A451%2Fannounce&tr=udp%3A%2F%2Ftracker.dler.org%3A6969%2Fannounce&tr=udp%3A%2F%2Fopen.stealth.si%3A80%2Fannounce&tr=udp%3A%2F%2Fopentracker.i2p.rocks%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker.gbitt.info%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fmovies.zsw.ca%3A6969%2Fannounce"
		 * );
		 */

		/* ****** GET DRIVER ****** */
		WebDriver webDriver = DriverFactory.getChromeDriver();
		/* ****** LOAD THE PAGE ****** */
		webDriver.get("https://www.google.com/");
		
		webDriver.manage().window().maximize();
		webDriver.navigate().to("https://pritambhansali.wixsite.com/portfolio/");
		webDriver.navigate().back();
		webDriver.navigate().forward();
		Thread.sleep(1000);
		webDriver.quit();
	}
}

`
---
`
		ChromeOptions options = new ChromeOptions();

		Map<String, Object> prefs = new HashMap<String, Object>();

		prefs.put("profile.default_content_setting_values.notifications", 2);

		// 1-Allow, 2-Block, 0-default

		options.setExperimentalOption("prefs", prefs);

		// System.setProperty("webdriver.chrome.driver",
		// "C:\\chromedriver_win32\\chromedriver_win32\\chromedriver.exe");

		// WebDriver driver = new ChromeDriver(options);
		WebDriver webDriver = DriverFactory.getChromeDriver(options);

		webDriver.get("http://www.spicejet.com");

`
