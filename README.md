import org.openqa.selenium.Cookie;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.remote.DesiredCapabilities;

public class PrivacyGuard {
    public static void main(String[] args) {
        // Specify the path to the ChromeDriver executable
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Disable third-party cookies
        ChromeOptions options = new ChromeOptions();
        options.addArguments("--disable-third-party-cookies");

        // Create a new instance of the ChromeDriver with the desired options
        DesiredCapabilities capabilities = DesiredCapabilities.chrome();
        capabilities.setCapability(ChromeOptions.CAPABILITY, options);
        ChromeDriver driver = new ChromeDriver(capabilities);

        // Example usage: navigate to a website and print the cookies
        driver.get("https://example.com");
        for (Cookie cookie : driver.manage().getCookies()) {
            System.out.println(cookie);
        }

        // Close the browser
        driver.quit();
    }
}
