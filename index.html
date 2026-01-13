// WeatherIsland.js - 独立天气插件
class WeatherIsland {
    constructor(options = {}) {
        this.options = {
            container: options.container || 'body',
            position: options.position || 'top-right', // top-right, top-left, bottom-right, bottom-left
            theme: options.theme || 'default', // default, dark, light
            refreshInterval: options.refreshInterval || 3600000, // 1小时
            showDetails: options.showDetails || true,
            enableMobile: options.enableMobile !== false, // 默认启用移动端
            ...options
        };
        
        this.weatherIcons = {
            '晴': '☀️',
            '多云': '⛅',
            '阴': '☁️',
            '小雨': '🌦️',
            '中雨': '🌧️',
            '大雨': '🌧️',
            '暴雨': '⛈️',
            '雷': '⚡',
            '雪': '❄️',
            '雾': '🌫️',
            '霾': '🌫️',
            '未知': '🌤️'
        };
        
        this.init();
    }

    async init() {
        await this.createWeatherWidget();
        await this.loadWeatherData();
        this.setupEventListeners();
        this.startAutoRefresh();
    }

    async createWeatherWidget() {
        // 创建桌面端圆形天气插件
        const circularWidget = document.createElement('div');
        circularWidget.className = 'circular-weather-widget';
        circularWidget.innerHTML = `
            <div class="weather-circle" style="background: ${this.getThemeBackground()}; border: 3px solid #fbbf24;">
                <div class="weather-content">
                    <div class="weather-icon">⛅</div>
                    <div class="weather-temp">24°C</div>
                    <div class="weather-location">北京市</div>
                </div>
            </div>
            <div class="weather-details" style="background: ${this.getThemeBackground()};">
                <div class="details-arrow"></div>
                <div class="details-condition">多云</div>
                <div class="details-grid">
                    <div class="details-item">湿度: 65%</div>
                    <div class="details-item right">风速: 12 km/h</div>
                    <div class="details-item">温度: 20～28°C</div>
                    <div class="details-item right">空气: 良</div>
                </div>
                <div class="details-update">更新: 14:30</div>
            </div>
        `;
        document.body.appendChild(circularWidget);

        // 创建移动端条形天气插件
        const mobileWidget = document.createElement('div');
        mobileWidget.className = 'weather-bar';
        mobileWidget.innerHTML = `
            <div class="bar-left">
                <div class="bar-icon">⛅</div>
                <div class="bar-info">
                    <div class="bar-temp">24°C</div>
                    <div class="bar-location">北京市</div>
                </div>
            </div>
            <div class="bar-details">多云 | 湿度: 65%</div>
        `;
        document.body.appendChild(mobileWidget);

        // 创建移动端详情面板（已移除关闭按钮）
        const mobileDetails = document.createElement('div');
        mobileDetails.className = 'mobile-details';
        mobileDetails.innerHTML = `
            <div class="mobile-details-content" style="background: ${this.getThemeBackground()};">
                <div class="mobile-icon">⛅</div>
                <div class="mobile-condition">多云</div>
                <div class="mobile-info">
                    <div class="mobile-info-item">
                        <div class="mobile-info-label">温度</div>
                        <div class="mobile-info-value">24°C</div>
                    </div>
                    <div class="mobile-info-item">
                        <div class="mobile-info-label">湿度</div>
                        <div class="mobile-info-value">65%</div>
                    </div>
                    <div class="mobile-info-item">
                        <div class="mobile-info-label">风速</div>
                        <div class="mobile-info-value">12 km/h</div>
                    </div>
                    <div class="mobile-info-item">
                        <div class="mobile-info-label">空气质量</div>
                        <div class="mobile-info-value">良</div>
                    </div>
                </div>
                <div class="mobile-update-time">更新: 14:30</div>
            </div>
        `;
        document.body.appendChild(mobileDetails);

        this.positionWidget();
        this.applyStyles();
    }

    getThemeBackground() {
        switch(this.options.theme) {
            case 'dark':
                return 'rgba(30, 30, 30, 0.95)';
            case 'light':
                return 'rgba(255, 255, 255, 0.95)';
            default:
                return 'rgba(255, 255, 255, 0.95)';
        }
    }

    positionWidget() {
        const circularWidget = document.querySelector('.circular-weather-widget');
        const weatherBar = document.querySelector('.weather-bar');

        // 根据选项设置位置
        switch(this.options.position) {
            case 'top-left':
                circularWidget.style.left = '20px';
                circularWidget.style.top = '20px';
                break;
            case 'bottom-right':
                circularWidget.style.right = '20px';
                circularWidget.style.bottom = '20px';
                circularWidget.style.top = 'auto';
                break;
            case 'bottom-left':
                circularWidget.style.left = '20px';
                circularWidget.style.bottom = '20px';
                circularWidget.style.top = 'auto';
                break;
            case 'top-right':
            default:
                circularWidget.style.right = '20px';
                circularWidget.style.top = '20px';
                break;
        }

        // 移动端条形始终在顶部
        weatherBar.style.top = '0';
        weatherBar.style.left = '0';
    }

    applyStyles() {
        // 添加必要的CSS样式
        if (!document.getElementById('weather-island-styles')) {
            const style = document.createElement('style');
            style.id = 'weather-island-styles';
            style.textContent = `
                .circular-weather-widget {
                    position: fixed;
                    z-index: 9999;
                    width: 120px;
                    height: 120px;
                    cursor: pointer;
                    transition: all 0.3s ease;
                }

                .weather-circle {
                    width: 100%;
                    height: 100%;
                    border-radius: 50%;
                    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
                    display: flex;
                    flex-direction: column;
                    justify-content: center;
                    align-items: center;
                    color: #333;
                    overflow: hidden;
                    transition: all 0.3s ease;
                }

                .weather-content {
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    justify-content: center;
                    text-align: center;
                    padding: 10px;
                }

                .weather-icon {
                    font-size: 42px;
                    line-height: 1;
                    margin-bottom: 5px;
                }

                .weather-temp {
                    font-size: 24px;
                    font-weight: bold;
                    margin-bottom: 2px;
                }

                .weather-location {
                    font-size: 12px;
                    opacity: 0.8;
                    white-space: nowrap;
                    overflow: hidden;
                    text-overflow: ellipsis;
                    max-width: 96px;
                }

                .weather-details {
                    position: absolute;
                    top: 50%;
                    right: calc(100% + 10px);
                    transform: translateY(-50%) scale(0.9);
                    width: max-content;
                    max-width: 200px;
                    min-width: 150px;
                    padding: 12px 16px;
                    border-radius: 12px;
                    display: flex;
                    flex-direction: column;
                    justify-content: center;
                    align-items: center;
                    opacity: 0;
                    visibility: hidden;
                    transition: all 0.3s ease;
                    text-align: center;
                    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
                    backdrop-filter: blur(10px);
                    z-index: 10000;
                    border: 1px solid rgba(0, 0, 0, 0.1);
                }

                .weather-details.active {
                    opacity: 1;
                    visibility: visible;
                    transform: translateY(-50%) scale(1);
                }

                .details-arrow {
                    position: absolute;
                    top: 50%;
                    right: -6px;
                    transform: translateY(-50%);
                    width: 0;
                    height: 0;
                    border-top: 6px solid transparent;
                    border-bottom: 6px solid transparent;
                    border-left: 6px solid rgba(255, 255, 255, 0.98);
                }

                .details-condition {
                    font-size: 14px;
                    font-weight: bold;
                    margin-bottom: 8px;
                    white-space: nowrap;
                }

                .details-grid {
                    display: grid;
                    grid-template-columns: 1fr 1fr;
                    gap: 6px 12px;
                    width: 100%;
                    margin-bottom: 8px;
                }

                .details-item {
                    font-size: 12px;
                    opacity: 0.8;
                    text-align: left;
                }

                .details-item.right {
                    text-align: right;
                }

                .details-update {
                    font-size: 10px;
                    opacity: 0.6;
                    margin-top: 4px;
                }

                .weather-bar {
                    position: fixed;
                    top: 0;
                    left: 0;
                    width: 100%;
                    background: rgba(255, 255, 255, 0.95);
                    backdrop-filter: blur(10px);
                    z-index: 9999;
                    padding: 10px 15px;
                    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
                    display: none;
                    align-items: center;
                    justify-content: space-between;
                    transition: all 0.3s ease;
                    height: 50px;
                    box-sizing: border-box;
                }

                .bar-left {
                    display: flex;
                    align-items: center;
                }

                .bar-icon {
                    font-size: 28px;
                    margin-right: 10px;
                }

                .bar-info {
                    display: flex;
                    flex-direction: column;
                }

                .bar-temp {
                    font-size: 18px;
                    font-weight: bold;
                }

                .bar-location {
                    font-size: 12px;
                    opacity: 0.8;
                }

                .bar-details {
                    font-size: 12px;
                    opacity: 0.7;
                    text-align: right;
                }

                .mobile-details {
                    position: fixed;
                    top: 0;
                    left: 0;
                    width: 100%;
                    height: 100%;
                    background: rgba(0, 0, 0, 0.7);
                    z-index: 10000;
                    display: flex;
                    flex-direction: column;
                    justify-content: center;
                    align-items: center;
                    opacity: 0;
                    visibility: hidden;
                    transition: all 0.3s ease;
                }

                .mobile-details.active {
                    opacity: 1;
                    visibility: visible;
                }

                .mobile-details-content {
                    background: white;
                    border-radius: 15px;
                    padding: 20px;
                    width: 80%;
                    max-width: 300px;
                    text-align: center;
                    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
                }

                .mobile-icon {
                    font-size: 48px;
                    margin-bottom: 10px;
                }

                .mobile-condition {
                    font-size: 20px;
                    font-weight: bold;
                    margin-bottom: 15px;
                }

                .mobile-info {
                    display: grid;
                    grid-template-columns: 1fr 1fr;
                    gap: 10px;
                    margin-bottom: 15px;
                }

                .mobile-info-item {
                    text-align: center;
                    padding: 8px;
                    background: #f5f5f5;
                    border-radius: 8px;
                }

                .mobile-info-label {
                    font-size: 12px;
                    opacity: 0.7;
                    margin-bottom: 4px;
                }

                .mobile-info-value {
                    font-size: 14px;
                    font-weight: bold;
                }

                .mobile-update-time {
                    font-size: 12px;
                    opacity: 0.6;
                }

                .loading {
                    display: inline-block;
                    width: 20px;
                    height: 20px;
                    border: 3px solid rgba(255,255,255,.3);
                    border-radius: 50%;
                    border-top-color: #fff;
                    animation: spin 1s ease-in-out infinite;
                }

                @keyframes spin {
                    to { transform: rotate(360deg); }
                }

                @media (max-width: 768px) {
                    .circular-weather-widget {
                        display: none;
                    }
                    
                    .weather-bar {
                        display: flex;
                    }
                }

                @media (min-width: 769px) {
                    .weather-bar {
                        display: none;
                        }
                    
                    .circular-weather-widget {
                        display: block;
                    }
                }
            `;
            document.head.appendChild(style);
        }
    }

    async loadWeatherData() {
        const now = Date.now();
        const CACHE_DURATION = this.options.refreshInterval;
        
        // 检查缓存
        const cacheKey = 'weatherIslandCache';
        const cachedData = localStorage.getItem(cacheKey);
        if (cachedData) {
            const cacheData = JSON.parse(cachedData);
            if (now - cacheData.lastUpdated < CACHE_DURATION) {
                this.updateWeatherDisplay(cacheData.data);
                return cacheData.data;
            }
        }

        try {
            const { location, coordinates } = await this.fetchUserLocation();
            if (!location || !coordinates) {
                const errorData = this.processWeatherData({ error: true, reason: '无法获取位置信息' }, now, '未知位置');
                this.updateWeatherDisplay(errorData);
                return errorData;
            }

            const weatherApiUrl = `https://api.open-meteo.com/v1/forecast?latitude=${coordinates.latitude}&longitude=${coordinates.longitude}&current=temperature_2m,weather_code,relative_humidity_2m,wind_speed_10m&daily=temperature_2m_max,temperature_2m_min&timezone=auto&forecast_days=1`;
            const airQualityApiUrl = `https://air-quality-api.open-meteo.com/v1/air-quality?latitude=${coordinates.latitude}&longitude=${coordinates.longitude}&current=european_aqi&timezone=auto`;

            const weatherController = new AbortController();
            const weatherTimeoutId = setTimeout(() => weatherController.abort(), 4000);
            const weatherResponse = await fetch(weatherApiUrl, {
                signal: weatherController.signal,
                headers: {
                    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36',
                    'Accept-Language': 'zh-CN,zh;q=0.9'
                }
            });
            clearTimeout(weatherTimeoutId);

            if (!weatherResponse.ok) {
                throw new Error(`获取天气信息失败: ${weatherResponse.status} ${weatherResponse.statusText}`);
            }

            const weatherData = await weatherResponse.json();

            let airQualityData = { current: { european_aqi: null } };
            try {
                const airQualityController = new AbortController();
                const airQualityTimeoutId = setTimeout(() => airQualityController.abort(), 5000);
                const airQualityResponse = await fetch(airQualityApiUrl, {
                    signal: airQualityController.signal,
                    headers: {
                        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36',
                        'Accept-Language': 'zh-CN,zh;q=0.9'
                    }
                });
                clearTimeout(airQualityTimeoutId);

                if (airQualityResponse.ok) {
                    airQualityData = await airQualityResponse.json();
                }
            } catch (airQualityError) {
                console.warn('获取空气质量数据时出错:', airQualityError);
            }

            const combinedData = {
                ...weatherData,
                current: {
                    ...weatherData.current,
                    european_aqi: airQualityData.current?.european_aqi
                }
            };

            const parsedWeatherData = this.processWeatherData(combinedData, now, location, coordinates);

            // 保存到缓存
            localStorage.setItem(cacheKey, JSON.stringify({
                data: parsedWeatherData,
                lastUpdated: now
            }));

            this.updateWeatherDisplay(parsedWeatherData);
            return parsedWeatherData;
        } catch (error) {
            console.error('获取天气信息失败:', error);
            const errorData = this.processWeatherData({ error: true, reason: error.message }, Date.now(), '未知位置');
            this.updateWeatherDisplay(errorData);
            return errorData;
        }
    }

    async fetchUserLocation() {
        try {
            let location = '';
            let coordinates = null;

            try {
                const controller = new AbortController();
                const timeoutId = setTimeout(() => controller.abort(), 4000);
                const myipLaResponse = await fetch('https://api.myip.la/cn?json', {
                    signal: controller.signal,
                    headers: {
                        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36',
                        'Accept-Language': 'zh-CN,zh;q=0.9'
                    }
                });
                clearTimeout(timeoutId);

                if (myipLaResponse.ok) {
                    const data = await myipLaResponse.json();
                    if (data && data.location) {
                        if (data.location.latitude && data.location.longitude) {
                            coordinates = {
                                latitude: parseFloat(data.location.latitude),
                                longitude: parseFloat(data.location.longitude)
                            };
                        }

                        const province = data.location.province || '';
                        const city = data.location.city || '';
                        if (province && city) {
                            if (city.includes(province.replace('省', '').replace('市', '').replace('都', ''))) {
                                location = city;
                            } else {
                                location = province + city;
                            }
                        } else if (province) {
                            location = province;
                        } else if (city) {
                            location = city;
                        } else if (data.location.country_name) {
                            location = data.location.country_name;
                        }
                    }
                }
            } catch (error) {
                console.warn('api.myip.la 获取失败，将回退到备用方案:', error.message);
            }

            if (!location) {
                try {
                    const ipipResponse = await fetch('https://myip.ipip.net', {
                        headers: {
                            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36',
                            'Referer': 'https://www.baidu.com/',
                            'Accept-Language': 'zh-CN,zh;q=0.9',
                            'Keep-Alive': 'yes',
                            'Cache-Control': 'no-cache'
                        }
                    });

                    if (ipipResponse.ok) {
                        const text = await ipipResponse.text();
                        if (text && text.includes('来自于：')) {
                            const locationPart = text.split('来自于：')[1];
                            if (locationPart) {
                                const locationInfo = locationPart.split(' ')[0];
                                if (locationInfo) {
                                    const parts = locationInfo.trim().split(' ');
                                    if (parts.length >= 3) {
                                        location = parts[1] + parts[2];
                                    } else if (parts.length === 2) {
                                        location = parts[1];
                                    } else {
                                        location = parts[0];
                                    }

                                    try {
                                        coordinates = await this.getCoordinates(location);
                                    } catch (geoError) {
                                        console.error(`获取 ${location} 坐标失败:`, geoError);
                                    }
                                }
                            }
                        }
                    }
                } catch (fallbackError) {
                    console.error('备用 API 也失败了:', fallbackError.message);
                }
            }

            if (!location) {
                console.warn('无法获取位置信息');
                return { location: '', coordinates: null };
            }

            return { location, coordinates };
        } catch (error) {
            console.error('获取位置信息过程中发生错误:', error);
            return { location: '', coordinates: null };
        }
    }

    async getCoordinates(cityName) {
        if (!cityName) return null;

        try {
            const geocodeUrl = `https://nominatim.openstreetmap.org/search?q=${encodeURIComponent(cityName)}&format=json&limit=1&accept-language=zh-Hans&countrycodes=CN`;

            const response = await fetch(geocodeUrl, {
                headers: {
                    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36',
                    'Accept-Language': 'zh-CN,zh;q=0.9'
                }
            });

            if (!response.ok) {
                throw new Error('地理编码请求失败');
            }

            const data = await response.json();
            if (data && data.length > 0) {
                const { lat, lon } = data[0];
                return { latitude: parseFloat(lat), longitude: parseFloat(lon) };
            }

            if (cityName.length > 2) {
                const province = cityName.substring(0, 2);
                const provinceUrl = `https://nominatim.openstreetmap.org/search?q=${encodeURIComponent(province)}&format=json&limit=1&accept-language=zh-Hans&countrycodes=CN`;
                const provinceResponse = await fetch(provinceUrl, {
                    headers: {
                        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36',
                        'Accept-Language': 'zh-CN,zh;q=0.9'
                    }
                });

                if (provinceResponse.ok) {
                    const provinceData = await provinceResponse.json();
                    if (provinceData && provinceData.length > 0) {
                        const { lat, lon } = provinceData[0];
                        return { latitude: parseFloat(lat), longitude: parseFloat(lon) };
                    }
                }
            }

            console.warn(`无法获取 ${cityName} 的坐标，天气服务暂不支持该地区`);
            return null;
        } catch (error) {
            console.error('获取坐标失败:', error);
            return null;
        }
    }

    processWeatherData(data, timestamp, userLocation = '', coordinates = null) {
        if (!data || data.error) {
            const errorMessage = data && data.reason ? data.reason : '该位置暂不支持';
            return {
                location: userLocation || '未知位置',
                condition: errorMessage,
                temperature: 'N/A',
                tempRange: 'N/A',
                airQuality: 'N/A',
                humidity: 'N/A',
                windSpeed: 'N/A',
                icon: this.weatherIcons['未知'],
                timestamp: timestamp
            };
        }

        const current = data.current || {};
        const weatherCode = current.weather_code || 0;
        const temperature = current.temperature_2m !== undefined ? `${Math.round(current.temperature_2m)}°C` : 'N/A';
        let tempRange = 'N/A';
        if (data.daily) {
            const minTemp = data.daily.temperature_2m_min?.[0];
            const maxTemp = data.daily.temperature_2m_max?.[0];
            if (minTemp !== undefined && maxTemp !== undefined) {
                tempRange = `${Math.round(minTemp)}～${Math.round(maxTemp)}°C`;
            }
        }

        let humidity = 'N/A';
        if (data.current && data.current.relative_humidity_2m !== undefined) {
            humidity = `${data.current.relative_humidity_2m}%`;
        }

        let airQuality = 'N/A';
        if (data.current && data.current.european_aqi !== undefined) {
            const aqi = data.current.european_aqi;
            let aqiLevel = '';
            if (aqi <= 20) aqiLevel = '优';
            else if (aqi <= 40) aqiLevel = '良';
            else if (aqi <= 60) aqiLevel = '中等';
            else if (aqi <= 80) aqiLevel = '一般';
            else if (aqi <= 100) aqiLevel = '差';
            else aqiLevel = '严重';
            airQuality = `${aqiLevel} (${aqi})`;
        }

        let windSpeed = 'N/A';
        if (data.current && data.current.wind_speed_10m !== undefined) {
            windSpeed = `${Math.round(current.wind_speed_10m)} km/h`;
        }

        let weatherCondition = '未知';
        let weatherIcon = this.weatherIcons['未知'];
        if (weatherCode !== undefined) {
            if (weatherCode === 0) {
                weatherCondition = '晴';
                weatherIcon = this.weatherIcons['晴'];
            } else if (weatherCode === 1) {
                weatherCondition = '大部晴朗';
                weatherIcon = this.weatherIcons['晴'];
            } else if (weatherCode === 2) {
                weatherCondition = '局部多云';
                weatherIcon = this.weatherIcons['多云'];
            } else if (weatherCode === 3) {
                weatherCondition = '多云';
                weatherIcon = this.weatherIcons['多云'];
            } else if ([45, 48].includes(weatherCode)) {
                weatherCondition = '雾';
                weatherIcon = this.weatherIcons['雾'];
            } else if ([51, 53, 55, 56, 57].includes(weatherCode)) {
                weatherCondition = '小雨';
                weatherIcon = this.weatherIcons['小雨'];
            } else if ([61, 63, 66, 80, 81].includes(weatherCode)) {
                weatherCondition = '中雨';
                weatherIcon = this.weatherIcons['中雨'];
            } else if ([65, 67, 82].includes(weatherCode)) {
                weatherCondition = '大雨';
                weatherIcon = this.weatherIcons['大雨'];
            } else if ([95, 96, 99].includes(weatherCode)) {
                weatherCondition = '雷雨';
                weatherIcon = this.weatherIcons['雷'];
            } else if ([71, 73, 75, 77, 85, 86].includes(weatherCode)) {
                weatherCondition = '雪';
                weatherIcon = this.weatherIcons['雪'];
            } else {
                weatherCondition = '阴';
                weatherIcon = this.weatherIcons['阴'];
            }
        }

        return {
            location: userLocation || '未知位置',
            condition: weatherCondition,
            temperature: temperature,
            tempRange: tempRange,
            airQuality: airQuality,
            humidity: humidity,
            windSpeed: windSpeed,
            icon: weatherIcon,
            color: '#94a3b8',
            timestamp: timestamp
        };
    }

    updateWeatherDisplay(weatherData) {
        this.updateCircularWidget(weatherData);
        this.updateBarWidget(weatherData);
        this.updateMobileDetails(weatherData);
    }

    updateCircularWidget(weatherData) {
        const circularWidget = document.querySelector('.circular-weather-widget');
        if (!circularWidget) return;

        const circle = circularWidget.querySelector('.weather-circle');
        const icon = circularWidget.querySelector('.weather-icon');
        const temp = circularWidget.querySelector('.weather-temp');
        const location = circularWidget.querySelector('.weather-location');
        const details = circularWidget.querySelector('.weather-details');
        const condition = details.querySelector('.details-condition');
        const humidity = details.querySelector('.details-item:nth-child(1)');
        const wind = details.querySelector('.details-item:nth-child(2)');
        const tempRange = details.querySelector('.details-item:nth-child(3)');
        const airQuality = details.querySelector('.details-item:nth-child(4)');
        const updateTime = details.querySelector('.details-update');

        if (circle) circle.style.borderColor = weatherData.color;
        if (icon) icon.textContent = weatherData.icon;
        if (temp) temp.textContent = weatherData.temperature;
        if (location) location.textContent = weatherData.location;
        if (condition) condition.textContent = weatherData.condition;
        if (humidity) humidity.textContent = `湿度: ${weatherData.humidity}`;
        if (wind) wind.textContent = `风速: ${weatherData.windSpeed}`;
        if (tempRange) tempRange.textContent = `温度: ${weatherData.tempRange}`;
        if (airQuality) airQuality.textContent = `空气: ${weatherData.airQuality.split(' ')[0]}`;

        if (updateTime) {
            const updateDate = new Date(weatherData.timestamp);
            updateTime.textContent = `更新: ${updateDate.getHours().toString().padStart(2, '0')}:${updateDate.getMinutes().toString().padStart(2, '0')}`;
        }
    }

    updateBarWidget(weatherData) {
        const barWidget = document.querySelector('.weather-bar');
        if (!barWidget) return;

        const icon = barWidget.querySelector('.bar-icon');
        const temp = barWidget.querySelector('.bar-temp');
        const location = barWidget.querySelector('.bar-location');
        const details = barWidget.querySelector('.bar-details');

        if (icon) icon.textContent = weatherData.icon;
        if (temp) temp.textContent = weatherData.temperature;
        if (location) location.textContent = weatherData.location;
        if (details) details.textContent = `${weatherData.condition} | 湿度: ${weatherData.humidity}`;
    }

    updateMobileDetails(weatherData) {
        const mobileDetails = document.querySelector('.mobile-details');
        if (!mobileDetails) return;

        const mobileIcon = mobileDetails.querySelector('.mobile-icon');
        const mobileCondition = mobileDetails.querySelector('.mobile-condition');
        const tempValue = mobileDetails.querySelector('.mobile-info-item:nth-child(1) .mobile-info-value');
        const humidityValue = mobileDetails.querySelector('.mobile-info-item:nth-child(2) .mobile-info-value');
        const windValue = mobileDetails.querySelector('.mobile-info-item:nth-child(3) .mobile-info-value');
        const airQualityValue = mobileDetails.querySelector('.mobile-info-item:nth-child(4) .mobile-info-value');
        const mobileUpdateTime = mobileDetails.querySelector('.mobile-update-time');

        if (mobileIcon) mobileIcon.textContent = weatherData.icon;
        if (mobileCondition) mobileCondition.textContent = weatherData.condition;
        if (tempValue) tempValue.textContent = weatherData.temperature;
        if (humidityValue) humidityValue.textContent = weatherData.humidity;
        if (windValue) windValue.textContent = weatherData.windSpeed;
        if (airQualityValue) airQualityValue.textContent = weatherData.airQuality.split(' ')[0];

        if (mobileUpdateTime) {
            const updateDate = new Date(weatherData.timestamp);
            mobileUpdateTime.textContent = `更新: ${updateDate.getHours().toString().padStart(2, '0')}:${updateDate.getMinutes().toString().padStart(2, '0')}`;
        }
    }

    setupEventListeners() {
        const circularWidget = document.querySelector('.circular-weather-widget');
        const circle = circularWidget ? circularWidget.querySelector('.weather-circle') : null;
        const details = circularWidget ? circularWidget.querySelector('.weather-details') : null;
        const barWidget = document.querySelector('.weather-bar');
        const mobileDetails = document.querySelector('.mobile-details');
        const mobileDetailsContent = mobileDetails ? mobileDetails.querySelector('.mobile-details-content') : null;

        if (circle && details) {
            // 桌面端悬停效果
            circle.addEventListener('mouseenter', () => {
                details.classList.add('active');
                circle.style.transform = 'scale(1.05)';
                circle.style.boxShadow = '0 8px 30px rgba(0, 0, 0, 0.25)';
            });

            circle.addEventListener('mouseleave', () => {
                details.classList.remove('active');
                circle.style.transform = 'scale(1)';
                circle.style.boxShadow = '0 4px 20px rgba(0, 0, 0, 0.15)';
            });

            // 点击圆形刷新
            circle.addEventListener('click', async () => {
                circle.classList.add('loading');
                try {
                    await this.loadWeatherData();
                } catch (error) {
                    console.error('刷新天气数据失败:', error);
                } finally {
                    circle.classList.remove('loading');
                }
            });
        }

        if (barWidget && mobileDetails) {
            // 移动端点击效果
            barWidget.addEventListener('click', () => {
                mobileDetails.classList.add('active');
            });

            // 修改：点击遮罩层（mobile-details）关闭面板
            mobileDetails.addEventListener('click', (event) => {
                // 如果点击的是遮罩层（而不是内容区域），则关闭面板
                if (event.target === mobileDetails) {
                    mobileDetails.classList.remove('active');
                }
            });

            // 修改：阻止点击内容区域时关闭面板（事件冒泡）
            if (mobileDetailsContent) {
                mobileDetailsContent.addEventListener('click', (event) => {
                    event.stopPropagation();
                });
            }
        }
    }

    startAutoRefresh() {
        setInterval(async () => {
            await this.loadWeatherData();
        }, this.options.refreshInterval);
    }

    // 提供手动刷新方法
    async refresh() {
        return await this.loadWeatherData();
    }

    // 销毁插件实例
    destroy() {
        const widgets = document.querySelectorAll('.circular-weather-widget, .weather-bar, .mobile-details');
        widgets.forEach(widget => widget.remove());
        const styles = document.getElementById('weather-island-styles');
        if (styles) styles.remove();
    }
}

// 自动初始化（如果需要自动启动的话）
if (typeof window !== 'undefined') {
    window.WeatherIsland = WeatherIsland;
}
