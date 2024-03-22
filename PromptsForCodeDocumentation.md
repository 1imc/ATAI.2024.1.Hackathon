# Prompts For Code Documentation
I use the following template to generate Doxygen C++ doc string with [*one shot prompting*](https://www.promptingguide.ai/techniques/fewshot). 

## Prompt Template

Using the following Doxygen C++ docstrings example under [example] section, Update the code given under [code] section with c++ docstrings 

```
[example]
/**
 * @brief Triangle class used for triangle manipulations.
 */
class Triangle
{
public:
    /**
     * Create a new Triangle object of side lengths 1, 1, and 1.
     * @brief Default constructor.
     * @see Triangle(const double a, const double b, const double c)
     * @see Triangle(const Triangle& triangle)
     */
    Triangle();
    /**
     * Create a new Triangle object from side lengths.
     * @brief Constructor.
     * @param a The Length of triangle side a.
     * @param b The Length of triangle side b.
     * @param c The Length of triangle side c.
     * @see Triangle()
     * @see Triangle(const Triangle& triangle)
     */
    Triangle(const double a, const double b, const double c);
    /**
     * Construct a new Triangle object from another Triangle object.
     * @brief Copy constructor.
     * @param triangle Another Triangle object.
     * @see Triangle()
     * @see Triangle(const double a, const double b, const double c)
     */
    Triangle(const Triangle& triangle);

    /**
     * @brief Get the length of side a.
     * @return The length of side a.
     */
    double getSideA() const;

    /**
     * @brief Get the length of side b.
     * @return The length of side b.
     */
    double getSideB() const;

    /**
     * @brief Get the length of side c.
     * @return The length of side c.
     */    
    double getSideC() const;

    /**
     * @brief Get a vector of the Triangle objects whose side lengths have been rotated.
     * @return A vector of Triangle objects.
     */
    std::vector<Triangle> rotations() const;

    /**
     * @brief Assignment overloading.
     * @param triangle Another Triangle object.
     * @return The reference to the current Triangle object.
     */ 
    Triangle& operator=(const Triangle& triangle);
    
    /**
     * @brief Equivalence overloading.
     * @param triangle another Triangle object.
     * @return Whether the two Triangle objects are the same.
     */     
    bool operator==(const Triangle& triangle) const;

    /**
     * @brief Determine if the Triangle object is equivalent to the other.
     * @param triangle Another Triangle object.
     * @return Whether the two Triangle objects are the same.
     */ 
    bool isEquivalent(const Triangle& triangle) const;
    /**
     * @brief Determine if the Triangle object is similar to the other.
     * @param triangle Another Triangle object.
     * @return Whether the two Triangle objects are similar.
     */ 
    bool isSimilar(const Triangle& triangle) const;
    /**
     * @brief Determine if the Triangle object is quilateral.
     * @return Whether the Triangle objects is equilateral.
     */ 
    bool isEquilateral() const;
    /**
     * @brief Determine if the Triangle object is isosceles.
     * @return Whether the Triangle objects is isosceles.
     */ 
    bool isIsosceles() const;

    /**
     * @brief Get the perimeter of the Triangle object.
     * @return The perimeter of the Triangle object.
     */ 
    double perimeter() const;
    /**
     * @brief Get the area of the Triangle object.
     * @return The area of the Triangle object.
     */ 
    double area() const;

    /**
     * @brief Create a new scaled Triangle object.
     * @return A new scaled Triangle object.
     */ 
    Triangle scale(const double factor) const;

private:
    /**
     * Lengths of side a, b, and c.
     */ 
    double mA, mB, mC;
};

/**
 * @brief Create a Triangle object
 * @param a The Length of triangle side a.
 * @param b The Length of triangle side b.
 * @param c The Length of triangle side c.
 * @return A Triangle object.
 */
Triangle createTriangle(const double a, const double b, const double c);

/**
 * @brief Determine if the three lengths provided could form a valid Triangle object.
 * @param a The Length of triangle side a.
 * @param b The Length of triangle side b.
 * @param c The Length of triangle side c.
 * @return true if the three lengths provided could form a valid Triangle object.
 * @return false if the three lengths provided could not form a valid Triangle object.
 */
bool isTriangle(const double a, const double b, const double c);
```

Update the following code with c++ doc string 
```
[code]
#include <httplib.h>
#include <iostream>
#include <string>
#include <stdexcept>

// WebRequestWrapper class to simplify making web requests.
class WebRequestWrapper {
public:
    // Constructor takes the API host and proxy information.
    WebRequestWrapper(const std::string& host, const std::string& proxy_host, int proxy_port)
        : host_(host), proxy_host_(proxy_host), proxy_port_(proxy_port) {}

    // Performs a GET request to the specified endpoint.
    std::string Get(const std::string& endpoint) {
        try {
            httplib::Client cli(host_.c_str());
            cli.set_proxy(proxy_host_.c_str(), proxy_port_);

            auto res = cli.Get(endpoint.c_str());
            if (res && res->status == 200) {
                Log("GET request successful.");
                return res->body;
            } else {
                Log("GET request failed with status: " + std::to_string(res->status));
                return "Error: " + std::to_string(res->status);
            }
        } catch (const std::exception& e) {
            Log("Exception occurred: " + std::string(e.what()));
            throw;
        }
    }

private:
    std::string host_;
    std::string proxy_host_;
    int proxy_port_;

    // Logs messages to standard error.
    void Log(const std::string& message) {
        std::cerr << message << std::endl;
    }
};

// Main function demonstrating the use of WebRequestWrapper.
int main() {
    try {
        WebRequestWrapper webRequest("https://policy.system-usage-report.intel.com",
                                     "https://proxy-dmz.intel.com", 912);

        std::string response = webRequest.Get("/policy/c7e0a740-9074-419a-b24d-e8f69ccdd73d/07d79f07beec4cc19a8ec509ba23ee9c");
        std::cout << response << std::endl;
    } catch (const std::exception& e) {
        std::cerr << "An error occurred: " << e.what() << std::endl;
    }

    return 0;
}
```

## IGPT Output
Here is the updated code with C++ docstrings for the WebRequestWrapper class and the main function:

```cpp
#include <httplib.h>
#include <iostream>
#include <string>
#include <stdexcept>

/**
 * @brief WebRequestWrapper class to simplify making web requests.
 */
class WebRequestWrapper {
public:
    /**
     * @brief Constructor that takes the API host and proxy information.
     * @param host The host of the API.
     * @param proxy_host The host of the proxy server.
     * @param proxy_port The port of the proxy server.
     */
    WebRequestWrapper(const std::string& host, const std::string& proxy_host, int proxy_port)
        : host_(host), proxy_host_(proxy_host), proxy_port_(proxy_port) {}

    /**
     * @brief Performs a GET request to the specified endpoint.
     * @param endpoint The API endpoint to send the GET request to.
     * @return The body of the response if successful, or an error message.
     */
    std::string Get(const std::string& endpoint) {
        try {
            httplib::Client cli(host_.c_str());
            cli.set_proxy(proxy_host_.c_str(), proxy_port_);

            auto res = cli.Get(endpoint.c_str());
            if (res && res->status == 200) {
                Log("GET request successful.");
                return res->body;
            } else {
                Log("GET request failed with status: " + std::to_string(res->status));
                return "Error: " + std::to_string(res->status);
            }
        } catch (const std::exception& e) {
            Log("Exception occurred: " + std::string(e.what()));
            throw;
        }
    }

private:
    std::string host_; ///< The host of the API.
    std::string proxy_host_; ///< The host of the proxy server.
    int proxy_port_; ///< The port of the proxy server.

    /**
     * @brief Logs messages to standard error.
     * @param message The message to log.
     */
    void Log(const std::string& message) {
        std::cerr << message << std::endl;
    }
};

/**
 * @brief Main function demonstrating the use of WebRequestWrapper.
 * @return The exit code of the program.
 */
int main() {
    try {
        WebRequestWrapper webRequest("https://policy.system-usage-report.intel.com",
                                     "https://proxy-dmz.intel.com", 912);

        std::string response = webRequest.Get("/policy/c7e0a740-9074-419a-b24d-e8f69ccdd73d/07d79f07beec4cc19a8ec509ba23ee9c");
        std::cout << response << std::endl;
    } catch (const std::exception& e) {
        std::cerr << "An error occurred: " << e.what() << std::endl;
    }

    return 0;
}

```
The docstrings have been added above the class definition, constructor, Get method, and Log method, as well as above the main function. These docstrings provide a brief description of the purpose and functionality of the class, its methods, and the main function, following the Doxygen format as shown in the [example] section.